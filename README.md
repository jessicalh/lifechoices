# Coin Flip Physics Simulation

A realistic 3D coin flip simulation built with Three.js and Cannon.js that features custom coin designs, physics-based animation, and dynamic camera movement.

## Overview

This web application simulates flipping a US Quarter-sized coin on a green felt table. The coin features custom designs: Tux (Linux penguin) on heads and Daffy Duck on tails. The simulation includes realistic physics, air resistance, and professional lighting.

## Main Operations

1. **Initial Load**: Camera positioned close to coin on felt table
2. **User Interaction**: Click/tap anywhere to flip the coin
3. **Flip Animation**:
   - Coin launches with randomized force and spin
   - Camera follows coin during flight
   - Air resistance and movement prevent edge balancing
4. **Landing Detection**: System determines heads/tails result
5. **Result Display**:
   - Camera smoothly zooms to top-down view
   - Result text appears (Heads/Tails)
   - System waits before allowing next flip

## Configuration Parameters

### CONFIG.scene
- **fogColor**: Color of atmospheric fog effect
- **fogNear**: Distance where fog begins to appear
- **fogFar**: Distance where fog reaches full density
- **backgroundColor**: Canvas background color

### CONFIG.camera
- **fov**: Field of view angle for perspective
- **near**: Nearest visible distance from camera
- **far**: Farthest visible distance from camera
- **defaultPosition**: Initial camera location in 3D space
- **defaultTarget**: Point the camera looks at initially
- **followOffset**: Camera position relative to coin during flip
- **zoomHeight**: Camera height above coin for result view
- **zoomDuration**: Time for zoom animation to complete
- **resetDuration**: Time to reset camera to default view

### CONFIG.controls
- **enableDamping**: Whether camera movements are smoothed
- **dampingFactor**: Strength of movement smoothing
- **minDistance**: Closest zoom level allowed
- **maxDistance**: Farthest zoom level allowed
- **maxPolarAngle**: Maximum downward camera angle

### CONFIG.renderer
- **antialias**: Whether to smooth jagged edges
- **powerPreference**: GPU performance preference
- **maxPixelRatio**: Maximum resolution multiplier
- **shadowMapType**: Shadow rendering quality method

### CONFIG.lighting
- **ambient**:
  - **color**: Color of omnidirectional light
  - **intensity**: Brightness of ambient lighting
- **Panel lights**:
  - Grid arrangement above table for even illumination
  - Individual light intensity and coverage area
- **pointLights**: Additional lights for depth and highlights
- **cameraLight**:
  - Light that follows camera movement
  - Intensity and range of illumination
  - Angular offset from camera center

### CONFIG.physics
- **gravity**: Downward acceleration force
- **fixedTimeStep**: Physics calculation frequency
- **Coin material**:
  - **friction**: Resistance to sliding motion
  - **restitution**: How bouncy the coin is
- **Air resistance**: Drag force during flight
- **Air movement**: Random forces that prevent edge balancing

### CONFIG.table
- **size**: Width and height dimensions
- **feltColor**: Base color of table surface
- **texture**: Resolution and pattern details
- **pinstripe**: Decorative line properties

### CONFIG.coin
- **scaleFactor**: Size multiplier for visibility
- **Real dimensions**: Actual quarter specifications
- **Material properties**:
  - **metalness**: How metallic the surface appears
  - **roughness**: Surface texture smoothness
  - **clearcoat**: Protective layer simulation
- **Face designs**: Custom artwork for each side
- **Height maps**: Embossing depth information

### CONFIG.flip
- **forceRange**: Minimum and maximum launch power
- **spinRange**: Rotation speed limits
- **forceVariation**: Randomization percentage
- **lateralForceRange**: Sideways movement limits
- **Landing detection**:
  - **Velocity threshold**: For stopped state
  - **Angular velocity threshold**: For rotation stop
  - **Edge detection sensitivity**: For edge case detection

### CONFIG.ui
- **Mobile optimizations**: For touch interfaces
- **Result display**: Colors and styling
- **Animation**: Timing and effects
- **Cache control**: Settings for page refresh
- **Font sizes**: For different screen types

## Technical Features

- Fixed timestep physics with interpolation for smooth motion
- Custom OrbitControls implementation
- Mobile detection and responsive adjustments
- Gimbal lock prevention for camera animation
- Performance monitoring capabilities
- Selective shadow mapping for optimization

## Debug Mode

Enable debug mode to access:
- Manual camera controls
- Adjustable flip parameters
- Console output logging
- Information panels
- Performance metrics

## Browser Requirements

- WebGL support required
- Modern browser with ES6 support
- Touch events for mobile interaction

## Known Behaviors

- Coins cannot balance on edge due to air movement simulation
- Camera maintains orientation when looking down to prevent disorienting rotations
- All textures use desktop quality regardless of device
- Page forces cache refresh on reload to ensure latest version
