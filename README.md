#include <iostream>
#include <map>
#include <string>

using namespace std;

// Function to convert grade to grade points
double getGradePoints(char grade) {
  switch (grade) {
    case 'A':
    case 'a':
      return 4.0;
    case 'B':
    case 'b':
      return 3.0;
    case 'C':
    case 'c':
      return 2.0;
    case 'D':
    case 'd':
      return 1.0;
    case 'F':
    case 'f':
      return 0.0;
    default:
      cout << "Invalid grade. Assuming F." << endl;
      return 0.0;
  }
}

int main() {
  int semesters;
  cout << "Enter the number of semesters: ";
  cin >> semesters;

  double totalCGPA = 0;
  int totalCredits = 0;

  for (int semester = 1; semester <= semesters; semester++) {
    cout << "\nSemester " << semester << ":" << endl;
    int courses;
    cout << "Enter the number of courses: ";
    cin >> courses;

    double semesterGPA = 0;
    int semesterCredits = 0;

    for (int course = 1; course <= courses; course++) {
      char grade;
      int credits;
      cout << "Enter grade for course " << course << " (A-F): ";
      cin >> grade;
      cout << "Enter credit hours for course " << course << ": ";
      cin >> credits;

      double gradePoints = getGradePoints(grade);
      semesterGPA += gradePoints * credits;
      semesterCredits += credits;

      cout << "Course " << course << ": Grade=" << grade << ", Credits=" << credits << endl;
    }

    semesterGPA /= semesterCredits;
    cout << "Semester GPA: " << semesterGPA << endl;

    totalCGPA += semesterGPA * semesterCredits;
    totalCredits += semesterCredits;

    cout << "Total Credits so far: " << totalCredits << endl;
    cout << "Total CGPA so far: " << totalCGPA / totalCredits << endl;
  }

  cout << "\nFinal CGPA: " << totalCGPA / totalCredits << endl;

  return 0;
}

