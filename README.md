hw1
# Function to calculate the largest rectangle area
def largest_rectangle_area(heights):
    max_area = 0
    stack = []
    heights.append(0)  # Append a zero to properly handle the remaining elements

    for i in range(len(heights)):
        while stack and heights[i] < heights[stack[-1]]:
            h = heights[stack.pop()]
            width = i if not stack else i - stack[-1] - 1
            max_area = max(max_area, h * width)
        stack.append(i)

    return max_area

# Main function to process input and perform required operations
def main():
    # Read the number of rectangles
    n = int(input())

    # Read the heights of rectangles
    heights = list(map(float, input().split()))

    # Calculate the largest rectangle area
    area = largest_rectangle_area(heights)

    # Implement other functionalities: DFS, BFS, Path from Root to Minimum Node, Nearest Treasure Found

    # Print the largest rectangle area
    print("Largest Rectangle Area:", area)

# Run the main function
if __name__ == "__main__":
    # Here's an example of how you could use the specific inputs you provided
    input_data = """7
    25.29 121.67
    Library 25.123 121.456
    StudentCenter 25.234 121.567
    ScienceBuilding 25.345 121.678
    Cafeteria 25.210 121.430
    Gym 25.280 121.570
    Stadium 25.200 121.480
    Auditorium 25.260 121.550"""

    # Split the multiline input into lines and use as input
    import io
    import sys

    sys.stdin = io.StringIO(input_data)
    
    main()
