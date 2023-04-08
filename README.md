# java_8_interview_question

import java.util.ArrayList;

import java.util.Comparator;

import java.util.List;

import java.util.stream.Collectors;

public class EmployeeListSortBasedOnId {

	public static void main(String[] args) {
		List<Employee> list = new ArrayList<>();
		list.add(new Employee(1, "firoj"));
		list.add(new Employee(3, "tanis"));
		list.add(new Employee(4, "dipu"));
		list.add(new Employee(2, "rohit"));
		list.add(new Employee(6, "ibney"));
		list.add(new Employee(5, "naeem"));
		// we use the list.sort method to sort the list of employees based on their
		// Id's.
		// Using comparator .comparingInt() method which is more efficient then using
		// the sorted method of the stream interface.
		list.sort(Comparator.comparingInt(Employee::getId));
		// When then print the sorted list of employee using the forEach() method.
		list.forEach(System.out::println);

		//
		List<Employee> sortedlistbasedOnId = list.stream().sorted(Comparator.comparing(Employee::getId))
				.collect(Collectors.toList());
		sortedlistbasedOnId.forEach(System.out::println);
	}

}

class Employee {

	private int id;
	private String name;

	public Employee(int id, String name) {
		super();
		this.id = id;
		this.name = name;
	}

	public int getId() {
		return id;
	}

	public void setId(int id) {
		this.id = id;
	}

	public String getName() {
		return name;
	}

	public void setName(String name) {
		this.name = name;
	}

	@Override
	public String toString() {
		return "Employee [id=" + id + ", name=" + name + "]";
	}

}
