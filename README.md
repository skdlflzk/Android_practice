# 안드로이드 튜토리얼

[link]: https://www.youtube.com/watch?v=kcTK3Ex6Ve4 "영상"

공부하자!


### NoActionBar

액션바를 없애자

``` xml
<style name="Theme.Tutorial" parent="Theme.MaterialComponents.DayNight.NoActionBar">
	<item name="android:windowFullscreen">screen</item>
</style>
```


### MotionLayout으로 변환하기
Design 에서 ConstraintLayout  오른클릭  convert to MotionLayout 
-> xml/~_scene.xml 이 생성된다.
Start ConstrainSet , End ConstraintSet, Transition

KeyFrameSet ? 특정 순간에 존재해야하는 생성

Design 화면에서 화살표를 클릭하면 Transition을 지정할 수 있는데,
+ Key Attribute를 통해
변경시킬 attribute를 선택할 수 있다.

``` xml
       <KeyFrameSet>
           <KeyAttribute
               motion:motionTarget="@+id/imageView"
               motion:framePosition="20"
               android:scaleX="0.7"
               android:scaleY="0.7" />
       </KeyFrameSet>
```

포지션과 scale은 수정 가능하다.

> 현재 상태에선 start와 end ConstraintSet이 비어있으므로(기본)
> framePosition="20" (%) 을 지난 후에는 나머지 80% 동안 기본으로 돌아간다(스케일이 0.7 ->1이 된다)


추가로 몇 개 추가하고

애니메이션을 어떻게 동작시킬지 손가락 버튼으로 트리거할 수 있다.



최종

``` xml
    <Transition
        motion:constraintSetEnd="@+id/end"
        motion:constraintSetStart="@id/start"
        motion:duration="1000">
       <KeyFrameSet>
           <KeyAttribute
               motion:motionTarget="@+id/imageView"
               motion:framePosition="20"
               android:scaleX="0.7"
               android:scaleY="0.7" />
           <KeyAttribute
               motion:motionTarget="@+id/imageView"
               motion:framePosition="50"
               android:scaleX="0.7"
               android:scaleY="0.7" />
           <KeyAttribute
               motion:motionTarget="@+id/imageView"
               motion:framePosition="100"
               android:scaleX="50"
               android:scaleY="50" />
       </KeyFrameSet>
        <OnClick motion:targetId="@+id/imageView" />
``
---------------
