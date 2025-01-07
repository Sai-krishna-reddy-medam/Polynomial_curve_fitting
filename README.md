# Polynomial_curve_fitting
import numpy as np
import matplotlib.pyplot as plt

# Function to get user input for data points
def get_points():
    print("Enter data points in the format: x1 y1, x2 y2, ..., xn yn")
    points = input("Enter points: ")
    points = points.strip().split(",")
    
    x = []
    y = []
    for point in points:
        xi, yi = map(float, point.strip().split())
        x.append(xi)
        y.append(yi)
    
    return np.array(x), np.array(y)

# Get data points from the user
x, y = get_points()

# Get the degree of the polynomial from the user
degree = int(input("Enter the degree of the polynomial: "))

# Fit polynomial
coefficients = np.polyfit(x, y, degree)

# Generate the polynomial equation
polynomial = np.poly1d(coefficients)

# Generate values for plotting the fitted curve
x_fit = np.linspace(min(x), max(x), 100)
y_fit = polynomial(x_fit)

# Plot original data points
plt.scatter(x, y, color='red', label='Data Points')

# Plot fitted curve
plt.plot(x_fit, y_fit, color='blue', label=f'Polynomial Fit (degree {degree})')

# Customize plot
plt.xlabel('X')
plt.ylabel('Y')
plt.title('Polynomial Curve Fitting')
plt.legend()
plt.grid()

# Show plot
plt.show()

# Print polynomial coefficients
print("\nPolynomial Coefficients:")
print(coefficients)

