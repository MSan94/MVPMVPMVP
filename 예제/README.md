## STEP1 Contract Interface는 왜 필요할까?!
- Contract Interface를 빼더라도 구현이 가능하긴 하다.
- 장점 
  - 문서의 역할
  - Presenter와 View 간 상호작용에 대한 설계를 도와준다.
  - 의사소통의 도움이 된다.
- 단점
  - 보일러플레이트 코드가 많아진다. -> Contract를 계속 생산
  - 코드 수정시 Contract를 고쳐야 함으로 오버헤드 발생

## STEP2 그럼 Contract는 무엇일까?!
- Contract 
  - Contract 인터페이스를 통해 View Interface, Presenter Interface 정의
  - BaseView, BasePresenter에는 모든 View와 Presenter에 공통적으로 들어갈 부분 정의
- View Interface
  - Activity or Fragment (View)에 상속
  - Presenter에서 View를 컨트롤할 때 사용
- 즉, Contract를 정의함으로서 대략적인 코드를 이해할 수 있다.

## STEP3 Google MVP 예제 알아보기
- BasePresenter
  - BasePresenter는 start()를 가지고 있다.
```
interface BasePresenter {
    fun start()
}
```
- BaseView
  - Presenter를  View에 전달하는 변수가 기본값으로 추가되어 있다.
```
interface BaseView<T> {

    var presenter: T

}
```
- Activity에서 Presenter를 생성하고, 이를 Fragment(View)에서 전달받아 동일한 Presenter를 양쪽에서 가지고 있도록 만들었습니다.

- Contract
```
interface TasksContract {

    interface View : BaseView<Presenter> {

        var isActive: Boolean

        fun setLoadingIndicator(active: Boolean)

        fun showTasks(tasks: List<Task>)

        fun showAddTask()

        fun showTaskDetailsUi(taskId: String)

        fun showTaskMarkedComplete()

        fun showTaskMarkedActive()

        fun showCompletedTasksCleared()

        fun showLoadingTasksError()

        fun showNoTasks()

        fun showActiveFilterLabel()

        fun showCompletedFilterLabel()

        fun showAllFilterLabel()

        fun showNoActiveTasks()

        fun showNoCompletedTasks()

        fun showSuccessfullySavedMessage()

        fun showFilteringPopUpMenu()
    }

    interface Presenter : BasePresenter {

        var currentFiltering: TasksFilterType

        fun result(requestCode: Int, resultCode: Int)

        fun loadTasks(forceUpdate: Boolean)

        fun addNewTask()

        fun openTaskDetails(requestedTask: Task)

        fun completeTask(completedTask: Task)

        fun activateTask(activeTask: Task)

        fun clearCompletedTasks()
    }
}
```
