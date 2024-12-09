import xarray as xr
import matplotlib.pyplot as plt

# Load the NetCDF file
nc_file_path = r'H:\saroj internship work\rainfall_data\data\1980_2020_cpc_jjas_mm.nc'
data = xr.open_dataset(nc_file_path)

# Extract the relevant data for the months June, July, August, and September
june_data = data.sel(time=data['time.month'] == 6)
july_data = data.sel(time=data['time.month'] == 7)
august_data = data.sel(time=data['time.month'] == 8)
september_data = data.sel(time=data['time.month'] == 9)

# Plotting
plt.figure(figsize=(12, 8))

plt.subplot(2, 2, 1)
june_data.mean(dim=('lat', 'lon')).precip.plot(label='June')
plt.title('June')

plt.subplot(2, 2, 2)
july_data.mean(dim=('lat', 'lon')).precip.plot(label='July')
plt.title('July')

plt.subplot(2, 2, 3)
august_data.mean(dim=('lat', 'lon')).precip.plot(label='August')
plt.title('August')

plt.subplot(2, 2, 4)
september_data.mean(dim=('lat', 'lon')).precip.plot(label='September')
plt.title('September')

plt.tight_layout()
plt.legend()
plt.show()
