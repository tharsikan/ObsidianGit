```typescript
'AppComponet {
	students: Student[];
	filteredStudents: Student[];
	_filterText: string ='';

	ngOnInit(){
		this.filteredStudents = this.students;
	}

	// when binding needs to read the value will be called
	get filterText(){
		return this._filterText;
	}

	// when binding needs to write the value will be called
	set filterText(value: string){
		this._filterText = value;
		this.filterdStuents = this.filterStudentByGender(value);
	}

	filterStudentByGender(filterTerm: string){
		if(this.students.length ===0 || this.filterText === ''){
			return this.students;
		} else{
			return this.students.filter((student)) =>
			{
				return student.gender.toLowerCase() ===   this.filterTerm.toLowerCase();
			}
		}
	}
}

```

```html
<input type="text" placeholder="Search by gender" [(ngModel)]="filerText">
<table id="student">
<tr>
	<th>Name</th>
	<th>Course</th>...
</tr>
<tr *ngFor="let std of filteredStudent">
	<td>{{std.name}}</td>
	<td>{{std.course}}</td>
	...
</tr><br>
<button (click)="AddDummyStudent()">Add student</button>

```