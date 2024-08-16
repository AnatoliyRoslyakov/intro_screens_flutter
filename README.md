# Animated Intro Pages

<p align="center">
  <video width="500" height="200" src="https://github.com/user-attachments/assets/d762d51e-bf8b-4784-9cf9-0131cb1fe30d"></video>
</p>

## Animation of Circles

<p align="center">
  <img src="https://github.com/user-attachments/assets/66b60639-9edc-47a5-9807-a3287314a190" alt="Animation of Circles">
</p>

## Code Example

```dart
@override
void initState() {
  super.initState();
  _step = widget.step;
  _currentAngle = widget.startAngel;
  _angleStep = 2 * pi / _step;
  _controller = AnimationController(
    duration: widget.duration,
    vsync: this,
  );
  _controller.addListener(() {
    setState(() {
      _currentAngle = _animation.value;
    });
  });
}

// click animation
void _animateQuarter({bool reverse = false}) {
  startAngle = _currentAngle;
  endAngle = _currentAngle + (reverse ? -_angleStep : _angleStep);
  _animation = Tween<double>(
    begin: startAngle,
    end: endAngle,
  ).animate(CurvedAnimation(
    parent: _controller,
    curve: widget.animation,
  ));
  reverse ? indexColor-- : indexColor++;
  _controller.forward(from: 0.0);
}

// moving in a circle
Transform.translate(
  offset: Offset(
    130 * _scale * cos(_currentAngle),
    140 * _scale * sin(_currentAngle),
  ),
  child: Container(
    width: 16,
    height: 16,
    decoration: BoxDecoration(
      color: _colors[indexColor].withOpacity(0.5),
      shape: BoxShape.circle,
      boxShadow: [
        BoxShadow(
          color: _colors[indexColor].withOpacity(0.3),
          spreadRadius: 2,
          blurRadius: 3,
        ),
      ],
    ),
  ),
),
```
## Carousel Slider ([carousel_slider](https://pub.dev/packages/carousel_slider))

<p align="center">
  <img src="https://github.com/user-attachments/assets/a69273b0-1191-449c-a845-50b521134808" alt="Animation Text">
</p>

```dart
 CarouselSlider(
                items: widget.sliderContent,
                carouselController: buttonCarouselController,
                options: CarouselOptions(
                  scrollPhysics: const NeverScrollableScrollPhysics(),
                  autoPlay: false,
                  enlargeCenterPage: true,
                  viewportFraction: 1,
                  aspectRatio: 2.0,
                  enlargeFactor: 0.6,
                  enlargeStrategy: CenterPageEnlargeStrategy.height,
                  initialPage: 0,
                ),
              ),
```

## Circular Step Progress Indicator ([step_progress_indicator](https://pub.dev/documentation/step_progress_indicator/latest/))

<p align="center">
  <img src="https://github.com/user-attachments/assets/a56d3123-624f-4380-83a3-6da13146499c" alt="Animation Text">
</p>


```dart
CircularStepProgressIndicator(
                      height: 70,
                      width: 70,
                      totalSteps: _step,
                      currentStep: indexColor + 1,
                      stepSize: 4,
                      padding: pi / 10,
                      unselectedColor: Colors.transparent,
                      selectedColor: _colors[indexColor],
                      roundedCap: (_, isSelected) => isSelected,
                      child: // button
```

