### Table of content
- [Table of content](#table-of-content)
- [Angular property binding](#angular-property-binding)
- [Working with forms](#working-with-forms)
- [Services](#services)

### Angular property binding
```
<app-task-item *ngFor="let task of tasks" [task]="task"/>
<div [ngClass]="..."/>

<fa-icon [ngStyle]="{'color': 'red'}" [icon]="faTimes" (click)="onDelete(task)"></fa-icon>

<app-button color="red" text="Add" (btnClick)="toggleAddTask()"></app-button>
```
These examples of HTML directives correspond to the class `Input()` and `Output()`:

```
export class TaskItemComponent implements OnInit {
	@Input() task!: Task;
	@Output() onDeleteTask: EventEmitter<Task> = new EventEmitter();
	...
}

export class ButtonComponent implements OnInit {
	@Input() text!: string;
	@Input() color!: string;
}
```

So I think:
1) `*ngFor` is not property binding.
2) `[task]`, `[ngClass]`, `[icon]`, are used to represent `Input()`
3) The brackets, `[]`, cause Angular to evaluate the right-hand side of the assignment as a dynamic expression. Without the brackets, Angular treats the right-hand side as a string literal and sets the property to that static value.
4) `(click)`, `(btnClick)` uses `()` for `Output()`, specifically event emitter.
5) Note interpolation `{{}}` often does the same thing.
All covered here in [Angular Official Docs](https://angular.io/guide/property-binding#property-binding-and-interpolation)
6) The two-way data binding `[(ngModel)] = "x"` must have `name="x"` of the same name.

### Working with forms
- Use `(ngSubmit)`, don't use form action tag, it saves the hassle of prevent defaults of events.

### Services
- In order to use a service, after you import it you must add it into the constructor, e.g. `private uiService: UiService`