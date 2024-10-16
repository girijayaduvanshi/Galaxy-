from astropy.io import fits
import numpy as np
import matplotlib.pyplot as plt
from skimage.restoration import denoise_bilateral

# Process Luminance (L) channel
luminance_files = [
    '2024-03-30_21-08-06_L_-10.10_10.00s_0000.fits', '2024-03-30_21-09-44_L_-9.80_10.00s_0000.fits'
]

# Stack Luminance FITS files
luminance_data = [fits.open(file)[0].data for file in luminance_files]
luminance_stacked = np.median(np.array(luminance_data), axis=0)

# Denoise the Luminance image
luminance_denoised = denoise_bilateral(luminance_stacked, sigma_color=0.05, sigma_spatial=15)

# Save the result to a new FITS file
fits.writeto('stacked_luminance.fits', luminance_denoised, fits.open(luminance_files[0])[0].header, overwrite=True)

# Display the result
plt.imshow(luminance_denoised, cmap='gray')
plt.title('Denoised Luminance Channel')
plt.show()

# Process Red (R) channel
red_files = [
    '2024-03-30_21-08-20_R_-10.00_10.00s_0000.fits', '2024-03-30_21-09-01_R_-9.90_10.00s_0000.fits'
]

# Stack Red FITS files
red_data = [fits.open(file)[0].data for file in red_files]
red_stacked = np.median(np.array(red_data), axis=0)

# Denoise the Red image
red_denoised = denoise_bilateral(red_stacked, sigma_color=0.05, sigma_spatial=15)

# Save the result to a new FITS file
fits.writeto('stacked_red.fits', red_denoised, fits.open(red_files[0])[0].header, overwrite=True)

# Display the result
plt.imshow(red_denoised, cmap='gray')
plt.title('Denoised Red Channel')
plt.show()
# Process Green (G) channel
green_files = [
    '2024-03-30_21-08-33_G_-9.90_10.00s_0000.fits', '2024-03-30_21-09-15_G_-9.90_10.00s_0000.fits'
]

# Stack Green FITS files
green_data = [fits.open(file)[0].data for file in green_files]
green_stacked = np.median(np.array(green_data), axis=0)

# Denoise the Green image
green_denoised = denoise_bilateral(green_stacked, sigma_color=0.05, sigma_spatial=15)

# Save the result to a new FITS file
fits.writeto('stacked_green.fits', green_denoised, fits.open(green_files[0])[0].header, overwrite=True)

# Display the result
plt.imshow(green_denoised, cmap='gray')
plt.title('Denoised Green Channel')
plt.show()
# Process Blue (B) channel
blue_files = [
    '2024-03-30_21-08-46_B_-9.90_10.00s_0000.fits', '2024-03-30_21-09-28_B_-9.80_10.00s_0000.fits'
]

# Stack Blue FITS files
blue_data = [fits.open(file)[0].data for file in blue_files]
blue_stacked = np.median(np.array(blue_data), axis=0)

# Denoise the Blue image
blue_denoised = denoise_bilateral(blue_stacked, sigma_color=0.05, sigma_spatial=15)

# Save the result to a new FITS file
fits.writeto('stacked_blue.fits', blue_denoised, fits.open(blue_files[0])[0].header, overwrite=True)

# Display the result
plt.imshow(blue_denoised, cmap='gray')
plt.title('Denoised Blue Channel')
plt.show()
