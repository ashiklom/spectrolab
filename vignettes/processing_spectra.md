# Processing spectra with spectrolab
Anna K. Schweiger and Jose Eduardo Meireles  


## Essential processing 

### Jump correction

Some instruments allow you to preserve the sensor overlap regions. This results in duplicated wavelenghts and a "jump" between the VIS/NIR and NIR/SWIR regions. `spectrolab`'s `jump corrector` removes the overlap regions between the VIS/NIR and NIR/SWIR regions, respectively, and corrects the spectra to allow for better transition between the regions, while keeping the spectral information as close to the original as possible. In principle, the algorithm searches for the wavelengths of closest approach in both overlap regions, cuts the spectrum into three pieces, removes the overlap and finds a multiplier to paste the junks back together. No additional smoothing is applied. As a convention, the NIR region is left unchanged, the VIS and SWIR get adjusted.  


```r
# Read Acer example spectra 
acer_spectra <- read_spectra(path = dir_path, format = "sig",   exclude_if_matches = c("BAD","WR"))

# and check result
plot(acer_spectra)

# Jump correction 
acer_juco <- jump_corr(acer_spectra)

# This looks better!
plot(acer_juco)
```

### Vector normalisation

Treating each spectrum as a vector and standarizing it to unity length is a great way to remove brightness differences (e.g. due to changing lamp power), while preserving the shape of the spectrum (and thus its information content). Vector normalization is implemented in `spectrolab`'s `normalize()` function. Note: If you want to use *Ms. A's* trait coefficients, you need to use vector normalized spectra, limited to the 400 - 2400 nm wavelength range.


```r
# Subset jump corrected spectra to 400 - 2400 nm 
acer_sub <- acer_juco[, 400:2400]

# and check result
plot(acer_sub)

# Perform vector normalization
acer_vn <- normalize(acer_sub)

# and check result
plot(acer_vn)
```

### Smoothing at overlap regions ... coming soon

Depending on your analysis, it can be a good idea to smooth remaining noise at the sensor overlap regions. 