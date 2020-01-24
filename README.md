# flutter_obj3d_test

An OBJ 3D Viewer and Parser for flutter/dart. Also a simple Rasterizer. 

## Usage
```
 Object3DViewer(
              refreshMilliseconds: 10,
              size: Size(ScreenUtils.width, ScreenUtils.height),
              animationController: _object3DViewerController,
              onHorizontalDragUpdate: (d) {
                if (_objIndex == 4)
                  _object3DViewerController.rotateY(d); //macska1
                else
                  _object3DViewerController.rotateZ(-d);
              },
              onVerticalDragUpdate: (d) {
                _object3DViewerController.rotateX(d);
              },
              initialZoom: _zooms[_objIndex],
              initialAngles: _angles[_objIndex],
              objPath: _objPaths[_objIndex],
              texturePath: _objTexturePaths[_objIndex],
              drawMode: _drawModes[_drawModeIndex],
              onZoomChangeListener: (zoom) => _zooms[_objIndex] = zoom,
              onRotationChangeListener: (Math.Vector3 angles) => _angles[_objIndex] = angles,
              color: _colors[_objIndex],
              showInfo: true,
              showWireframe: _showWireframe,
              wireframeColor: Colors.red,
              panDistanceToActivate: 40,
            ),
```

## Example

https://github.com/klaszlo8207/Flutter-OBJ-3D-Viewer/blob/master/lib/main.dart
            
## Usage
  ```
  const Object3DViewer({
    @required this.size,    //size of the widget
    @required this.objPath, //path of the obj file, assets or sd card
    @required this.initialZoom, //initial zoom
    @required this.refreshMilliseconds, 
    @required this.animationController, //controller for the animation
    this.texturePath, //the texture path
    this.showInfo = false, //info of the obj
    this.showWireframe = false,
    this.wireframeColor = Colors.black,
    this.animateRotateX = false, //rotate and animate the model
    this.animateRotateY = false,
    this.animateRotateZ = false,
    this.initialAngles, //the initial angles
    this.drawMode = DrawMode.SHADED, //drawmode: SHADED, WIREFRAME, TEXTURED
    this.onHorizontalDragUpdate, 
    this.onVerticalDragUpdate,
    this.panDistanceToActivate, //the distance when to activate the swype
    this.onZoomChangeListener, //zoom listener
    this.onRotationChangeListener, //rotation listener
    this.color,
  });
```  
## Limits            

**Please use this library with TRIANGLES in the obj file itself. **
Tha library can handle only some types in the obj file like: vertices, textCoords, normals, faces. 
Can handle minus face indices. If your model not in Triangle mode then you can convert that via Autodesk 3ds Max or other softwares.

Also this library can handle only a few Vertices in wireframe/shaded mode (Max vertices in these modes are about 5000 vertices)

**In textured mode the library is in EXPERIMENTAL mode, this is very poor quality yet.** 
In this mode you can set fewer vertices (like a cube) and do not want to zoom in, because the fill points will be very slow because the rasterizer algorithm at the moment. 




