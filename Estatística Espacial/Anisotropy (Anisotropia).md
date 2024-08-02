#IC 
- **Isotropy:** association only depends upon distance
- **Anisotropy:** association that depends upon the separation vector (***d***) between locations. As a result, association depends upon direction

Here, we explore covariance functions that are stationary but not isotropic.

### Isotropy vs. Anisotropy

### Anisotropy

- **Definition**: Anisotropy occurs when the spatial correlation or variability of a variable depends on the direction. This means that the spatial structure changes with direction.
- **Types of Anisotropy**:
    - **Geometric Anisotropy**: The range of spatial correlation varies with direction, but the sill (overall variance) remains the same.
    - **Sill Anisotropy**: Both the range and the sill vary with direction.
- **Implications**: When modeling a spatial process with anisotropy, different directions need to be treated differently. The variogram or covariance function will change depending on the direction of the spatial lag.
- **Example**: Consider measuring pollution levels in a city with a prevailing wind direction. The pollution levels might show a different pattern of variability along the direction of the wind compared to across the wind. This would be an example of anisotropy.

<aside>
📖 Anisotropy is the structural property of non-uniformity in different directions, as opposed to isotropy. An anisotropic object or pattern has properties that differ according to direction of measurement

</aside>

![Untitled](Untitled%2028.png)

![Untitled](Untitled%2029.png)

