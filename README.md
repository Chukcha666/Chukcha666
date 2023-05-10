Решение на C++:

#include <iostream>

#include <fstream>

#include <vector>

#include <string>

using namespace std;

struct Student {

    string fio;

    int course;

    int group;

    int result;

};

int main() {

    ifstream fin("input.txt");

    vector<Student> students;

    // Чтение данных из файла

    while (!fin.eof()) {

        Student s;

        fin >> s.fio >> s.course >> s.group >> s.result;

        students.push_back(s);

    }

    fin.close();

    vector<Student> good_students;

    int norm = 240; // норматив по бегу

    // Отбор студентов, выполневших норматив

    for (auto s : students) {

        if (s.result <= norm) {

            good_students.push_back(s);

        }

    }

    ofstream fout("output.txt");

    // Запись результата в файл

    for (auto s : good_students) {

        fout << s.fio << " " << s.course << " " << s.group << " " << s.result << endl;

    }

    fout.close();

    return 0;

}
