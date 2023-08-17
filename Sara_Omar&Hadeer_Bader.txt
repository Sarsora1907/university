#include <iostream>
#include<vector>
#include<fstream>
#include<bits/stdc++.h>
using namespace std;
class person     //abstract class
{
public :
	string name;
	int age;
	int id;
	virtual void role() = 0;         //virtual function
};
class student : public person    //inhertance
{
public :
	float gpa;
	void role()        //print the role of student
	{
		cout << "STUDY" << endl;
	}
};
class instructor :public person
{
public :
    string ins_name;
	int ins_salary;
	int houres;
	void role()
	{
		cout << "TEACHE" << endl;
	}
};
class employee :public person
{
public:
    string emp_name;
	int emp_salary;
	void role()
	{
		cout << "WORK" << endl;
	}
};
class manager :public person      //singleton class
{
	int salary;
	static manager* instance;            //pointer instance of type manager
	manager()
	{
	};

public:
	static manager* getsalary()      //function of type manager

	{
		if (instance == nullptr)        //if instance equal nothing create new object
		{
			instance = new manager();
		}
		return instance;
	}
	void role()
	{
		cout << "MANAGE" << "\n";
	}
	void setsalary(int s)     //function to set salary
	{
		salary = s;

	}
	int getsalar()   //function to get salary
	{
		return salary;
	}

};
class course
{
public :
	string course_title;
	int course_id;
	void details()
	{
		cout << "COURSE DETAILS IS" << endl;
	}
};
class department
{
public:
	string deprt_titile;
	vector <course>cources;       //vector for courses

	void details(course)
	{
		ifstream addd_course("courses.txt");  //write in the file
		if (!addd_course)
		{
			cout << "error for reading" << "\n";

		}
		string lines;
		cout << "there are your courses" << "\n";
		while (getline(addd_course, lines))
		{
			cout << lines << endl;
		}
	}
	void addcourse(course c)
	{

		cout << "please enter the course you want to add" << "\n";
		getline(cin, c.course_title);
		cources.push_back(c);
		ofstream add_course("courses.txt");   //read the file

		if (!add_course)
		{
			cout << "error for reading" << "\n";

		}

		add_course << endl << c.course_title;
		add_course.close();



	}

};
class faculty
{
public :
  string F_title;
  vector <student> students;
  vector <instructor> instructors;
  vector <employee> employees;
  vector <department> departments;
  void details(student)
  {
      ifstream add_student("students.txt");
      if(!add_student)
      {
          cout<<"error for information"<<endl;
      }
      string lines;
      while(getline(add_student,lines))
      {
          cout<<lines<<endl;
      }
  }
  void addStudent(student s)
  {
    cout << "please enter the students you want to add" << "\n";
		getline(cin,s.name);
		students.push_back(s);
		ofstream addStudent("students.txt");

		if (!addStudent)
		{
			cout << "error for reading" << "\n";

		}

		addStudent << endl << s.name;
		addStudent.close();

  }
  void details(employee)
  {
      ifstream add_employee("employees.txt");
      if(!add_employee)
      {
          cout<<"error for information"<<endl;
      }
      string lines;
      while(getline(add_employee,lines))
      {
          cout<<lines<<endl;
      }
  }
  void addEmp(employee e)
  {
    cout << "please enter the employees you want to add" << "\n";
		getline(cin, e.emp_name);
		employees.push_back(e);
		ofstream addEmp("employees.txt");

		if (!addEmp)
		{
			cout << "error for reading" << "\n";

		}

		addEmp << endl << e.emp_name;
		addEmp.close();

  }
  void details(instructor)
  {
      ifstream addInss("instructors.txt");
      if(!addInss)
      {
          cout<<"error for information"<<endl;
      }
      string lines;
      while(getline(addInss,lines))
      {
          cout<<lines<<endl;
      }
  }
  void addIns(instructor I)
  {
    cout << "please enter the instructors you want to add" << "\n";
		getline(cin, I.ins_name);
		instructors.push_back(I);
		ofstream addInss("instructors.txt");

		if (!addInss)
		{
			cout << "error for reading" << "\n";

		}

		addInss << endl << I.ins_name;
		addInss.close();

  }
  void details(department)
  {
      ifstream add_dep("departments.txt");
      if(!add_dep)
      {
          cout<<"error for information"<<endl;
      }
      string lines;
      while(getline(add_dep,lines))
      {
          cout<<lines<<endl;
      }
  }
  void addDep(department d)
  {
    cout << "please enter the departments you want to add" << "\n";
		getline(cin, d.deprt_titile);
		departments.push_back(d);
		ofstream addDep("departments.txt");

		if (!addDep)
		{
			cout << "error for reading" << "\n";

		}

		addDep << endl << d.deprt_titile;
		addDep.close();

  }


};
class university
{
    public :
    string uni_title;
    vector <faculty> faculties;
    manager* mn;
    void details(faculty)
    {
        ifstream add_faculties("faculties.txt");
      if(!add_faculties)
      {
          cout<<"error for information"<<endl;
      }
      string lines;
      while(getline(add_faculties,lines))
      {
          cout<<lines<<endl;
      }
    }
    void addfaculties(faculty F)
    {
      cout << "please enter the faculties you want to add" << "\n";
		getline(cin, F.F_title);
		faculties.push_back(F);
		ofstream addfaculties("faculties.txt");

		if (!addfaculties)
		{
			cout << "error for reading" << "\n";

		}

		addfaculties << endl << F.F_title;
		addfaculties.close();


    }

};
manager *manager :: instance=nullptr;
int main()
{
 string choice;
    cout<<"********************welcome to unversity system***************"<<"\n";
    cout<<"if you want to add faculty enter 1"<<"\n";
    cout<<"if you want to add course enter 2"<<"\n";
    cout<<"if you want to add student enter 3"<<"\n";
    cout<<"if you want to add employee enter 4"<<"\n";
    cout<<"if you want to add instructor enter 5"<<"\n";
    cout<<"if you want to add department enter 6"<<"\n";

    getline(cin,choice);
    university un;
    faculty fa;
    student st;
    employee em;
    instructor ins;
    course co;
    department de;

    if(choice=="1")
    {
        un.addfaculties(fa);
        un.details(fa);

    }

    else if(choice=="2")
    {
        de.addcourse(co);
        de.details(co);
    }
    else if(choice=="3")
    {
        fa.addStudent(st);
        fa.details(st);
    }
    else if(choice=="4")
    {

        fa.addEmp(em);
        fa.details(em);
    }
    else if(choice=="5")
    {
        fa.addIns(ins);
        fa.details(ins);
    }
    else if (choice=="6")
    {

        fa.addDep(de);
        fa.details(de);
    }
    else
    {

        cout<<"please enter a correct number from 1 to 6"<<"\n";


    }



return 0;
}
