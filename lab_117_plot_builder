import matplotlib.pyplot as plt
import numpy as np

data = [
    (20.2, 0.776, 0.008),
    (25.2, 1.498, 0.009),
    (34.0, 2.947, 0.021),
    (41.1, 4.161, 0.032),
    (48.6, 5.252, 0.037),
    (53.4, 5.853, 0.040),
    (59.9, 6.997, 0.049)
]


# Recalculate data for tau and a', with theta in degrees
def calculate_tau(theta_deg):
    theta_rad = np.radians(theta_deg)
    return np.tan(theta_rad)


def calculate_a_prime(a, theta_deg):
    theta_rad = np.radians(theta_deg)
    return a / np.cos(theta_rad)

# Custom line parameters for a' = g(tau - mu)
g = 9.160
mu = 0.282

def calculate_red_line(tau, g, mu):
    return g * (tau - mu)

theta_values, a_values, y_errors = zip(*data)

tau_values = [calculate_tau(theta) for theta in theta_values]
a_prime_values = [calculate_a_prime(a, theta) for a, theta in zip(a_values, theta_values)]

fig, ax = plt.subplots()

# whether to connect dots with a line
connect_dots = True

# Plot the data with error bars (serifs)
ax.errorbar(tau_values, a_prime_values, yerr=y_errors, fmt='o', capsize=3, label="Data points")

if connect_dots:
    ax.plot(tau_values, a_prime_values, linestyle='-', linewidth=3, color='blue', label="Data Line")  # Thicker line

# Calculate a' for the second line a' = g(tau - mu)
custom_a_prime_values = [calculate_red_line(tau, g, mu) for tau in tau_values]

# Plot the custom line for a' = g(tau - mu)
ax.plot(tau_values, custom_a_prime_values, linestyle='--', linewidth=2, color='red',
        label=f"Custom Line: $a' = {g}(\tau - {mu})$")

ax.set_xlabel(r"$\tau = \tan(\theta)$", fontsize=12)
ax.set_ylabel(r"$a' = \frac{a}{\cos(\theta)}$", fontsize=12)

ax.grid(True)

ax.legend()

plt.show()
