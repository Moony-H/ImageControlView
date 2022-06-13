# ImageControlView

<br/>

이미지를 회전, 확대 및 축소, 삭제 할 수 있는 ImageControlView를 만들었습니다.

아래는 실제 구동 화면 입니다.

<br/>


![ezgif com-gif-maker (1)](https://user-images.githubusercontent.com/53536205/173427966-359d62b2-4bff-4e7c-bfdd-038f4bf9ce3a.gif)


<br/>

## 사용시 주의사항

### 1. ImageControlView의 Parent는 반드시 ImageControlLayout 이어야 합니다.

<br/>

ImageControlView의 Focus(지금 사용자와 상호작용 하는 View)를 관리하기 위해서 ImageControlView는 ImageControlLayout을 부모 뷰로 가지고 있어야 합니다.

그렇지 않으면 IllegalStateException("ImageControlView's parent must be ImageControlLayout")을 발생 시킵니다.

<br/>

```kotlin
val p=this.parent

if(p is ImageControlLayout)
    parentLayout=p
else
    throw IllegalStateException("ImageControlView's parent must be ImageControlLayout")
```

<br/>

### 2. ImageControlLayout은 ConstraintLayout의 상속 입니다.

<br/>

ImageControlLayout은 ConstraintLayout을 상속하여 만들었습니다.

따라서 ImageControlView 뿐만 아니라 다른 View들도 자식으로 가질 수 있습니다.

ConstraintLayout처럼 사용해도 무방 합니다.

```xml
<?xml version="1.0" encoding="utf-8"?>

<com.moony.routeen.ui.view.other.ImageControlLayout

    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/activity_main_parent"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    >
    <com.moony.routeen.ui.view.other.ImageControlView
        android:layout_width="100dp"
        android:layout_height="100dp"
        app:src="@color/yellow"
        />

    <Button
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintLeft_toLeftOf="parent"
        app:layout_constraintRight_toRightOf="parent"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"/>
    
    <EditText
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintLeft_toLeftOf="parent"
        />





</com.moony.routeen.ui.view.other.ImageControlLayout>
```
