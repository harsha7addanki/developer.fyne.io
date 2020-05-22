---
layout: page
tags: [api]
title: Fyne API test
---

# test
--
    import "fyne.io/fyne/test"

Package test provides utility drivers for running UI tests without rendering

## Usage

#### func  ApplyTheme

```go
func ApplyTheme(t *testing.T, theme fyne.Theme)
```
ApplyTheme sets the given theme and waits for it to be applied to the current
app.

#### func  AssertCanvasTappableAt

```go
func AssertCanvasTappableAt(t *testing.T, c fyne.Canvas, pos fyne.Position) bool
```
AssertCanvasTappableAt asserts that the canvas is tappable at the given
position.

#### func  AssertImageMatches

```go
func AssertImageMatches(t *testing.T, masterFilename string, img image.Image, msgAndArgs ...interface{}) bool
```
AssertImageMatches asserts that the given image is the same as the one stored in
the master file. The master filename is relative to the `testdata` directory
which is relative to the test. The test `t` fails if the given image is not
equal to the loaded master image. In this case the given image is written into a
file in `testdata/failed/<masterFilename>` (relative to the test). This path is
also reported, thus the file can be used as new master.

#### func  AssertNotificationSent

```go
func AssertNotificationSent(t *testing.T, n *fyne.Notification, f func())
```
AssertNotificationSent allows an app developer to assert that a notification was
sent. After the content of f has executed this utility will check that the
specified notification was sent.

#### func  Canvas

```go
func Canvas() fyne.Canvas
```
Canvas returns a reusable in-memory canvas used for testing

#### func  LaidOutObjects

```go
func LaidOutObjects(o fyne.CanvasObject) (objects []fyne.CanvasObject)
```
LaidOutObjects returns all fyne.CanvasObject starting at the given
fyne.CanvasObject which is laid out previously.

#### func  MoveMouse

```go
func MoveMouse(c fyne.Canvas, pos fyne.Position)
```
MoveMouse simulates a mouse movement to the given position.

#### func  NewApp

```go
func NewApp() fyne.App
```
NewApp returns a new dummy app used for testing. It loads a test driver which
creates a virtual window in memory for testing.

#### func  NewClipboard

```go
func NewClipboard() fyne.Clipboard
```
NewClipboard returns a single use in-memory clipboard used for testing

#### func  NewDriver

```go
func NewDriver() fyne.Driver
```
NewDriver sets up and registers a new dummy driver for test purpose

#### func  NewDriverWithPainter

```go
func NewDriverWithPainter(painter SoftwarePainter) fyne.Driver
```
NewDriverWithPainter creates a new dummy driver that will pass the given painter
to all canvases created

#### func  NewTheme

```go
func NewTheme() fyne.Theme
```
NewTheme returns a new testTheme.

#### func  NewWindow

```go
func NewWindow(content fyne.CanvasObject) fyne.Window
```
NewWindow creates and registers a new window for test purposes

#### func  NewWindowWithPainter

```go
func NewWindowWithPainter(content fyne.CanvasObject, painter SoftwarePainter) fyne.Window
```
NewWindowWithPainter creates and registers a new window for test purposes

#### func  Tap

```go
func Tap(obj fyne.Tappable)
```
Tap simulates a left mouse click on the specified object.

#### func  TapAt

```go
func TapAt(obj fyne.Tappable, pos fyne.Position)
```
TapAt simulates a left mouse click on the passed object at a specified place
within it.

#### func  TapCanvas

```go
func TapCanvas(c fyne.Canvas, pos fyne.Position)
```
TapCanvas taps at an absolute position on the canvas.

#### func  TapSecondary

```go
func TapSecondary(obj fyne.SecondaryTappable)
```
TapSecondary simulates a right mouse click on the specified object.

#### func  TapSecondaryAt

```go
func TapSecondaryAt(obj fyne.SecondaryTappable, pos fyne.Position)
```
TapSecondaryAt simulates a right mouse click on the passed object at a specified
place within it.

#### func  Type

```go
func Type(obj fyne.Focusable, chars string)
```
Type performs a series of key events to simulate typing of a value into the
specified object. The focusable object will be focused before typing begins. The
chars parameter will be input one rune at a time to the focused object.

#### func  TypeOnCanvas

```go
func TypeOnCanvas(c fyne.Canvas, chars string)
```
TypeOnCanvas is like the Type function but it passes the key events to the
canvas object rather than a focusable widget.

#### func  WidgetRenderer

```go
func WidgetRenderer(wid fyne.Widget) fyne.WidgetRenderer
```
WidgetRenderer allows test scripts to gain access to the current renderer for a
widget. This can be used for verifying correctness of rendered components for a
widget in unit tests.

#### func  WithTestTheme

```go
func WithTestTheme(t *testing.T, f func())
```
WithTestTheme runs a function with the testTheme temporarily set.

#### type SoftwarePainter

```go
type SoftwarePainter interface {
	Paint(fyne.Canvas) image.Image
}
```

SoftwarePainter describes a simple type that can render canvases

#### type WindowlessCanvas

```go
type WindowlessCanvas interface {
	fyne.Canvas

	Resize(fyne.Size)

	Padded() bool
	SetPadded(bool)
}
```

WindowlessCanvas provides functionality for a canvas to operate without a window

#### func  NewCanvas

```go
func NewCanvas() WindowlessCanvas
```
NewCanvas returns a single use in-memory canvas used for testing

#### func  NewCanvasWithPainter

```go
func NewCanvasWithPainter(painter SoftwarePainter) WindowlessCanvas
```
NewCanvasWithPainter allows creation of an in-memory canvas with a specific
painter. The painter will be used to render in the Capture() call.