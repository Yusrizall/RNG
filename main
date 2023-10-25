#include <iostream>
#include <ctime>
#include <cstdlib>

using namespace std;

int percobaan,
    batasAtas,
    batasBawah,
    tebak,
    angkaRahasia,
    inputMax;

bool bermain,
     ketemu,
     quitAble;

char cUlang;

int cariAngka(int maksimal){
    int angka = (rand() % maksimal) + 1;
    return angka;
}

void acak(){
    srand(static_cast<unsigned int>(time(nullptr)));
}

void inisialisasi(){
    ketemu = false;
    percobaan = 0;
    batasBawah = 0;
}

int setting(){
    cout << " ! Masukkan batas maksimal angka yang ingin diacak ! :";
    cin >> inputMax;
    batasAtas = inputMax;
    return inputMax;
}

void kalimat(string kunci){
    if(kunci == "welcome"){
        cout << "+----------------------------+\n";
        cout << "| Selamat Datang di game RNG |\n";
        cout << "| + Random Number Guesser! + |\n";
        cout << "+----------------------------+\n";
    }else if(kunci == "tebak"){
        cout << "(Total percobaan anda: " << percobaan << ")\n";
        cout << "---> Silahkan menebak angka diantara [" << batasBawah << "] - [" << batasAtas << "] :";
    }else if(kunci == "opsiQuit"){
        cout << "\ninput '-1' untuk quit (menyerah).\n";
    }else if(kunci == "menang"){
        cout << "Selamat ! Kamu berhasil menebak angka rahasia : " << angkaRahasia << endl << endl;
    }else if(kunci == "kalah"){
        cout << "Sayang sekali, angka rahasia adalah : " << angkaRahasia << endl;
    }else if(kunci == "OBA"){
        cout << "Tebakan tidak boleh melebihi batas atas (" << batasAtas << ") !\n\n";
    }else if(kunci == "OBB"){
        cout << "Tebakan tidak boleh kurang dari batas bawah (" << batasBawah << ") !\n\n";
    }else if(kunci == "BA"){
        cout << "Tebakan anda diatas angka rahasia." << "\n\n";
        batasAtas = tebak;
        percobaan++;
    }else if(kunci == "BB"){
        cout << "Tebakan anda dibawah angka rahasia." << "\n\n";
        batasBawah = tebak;
        percobaan++;
    }
}

void menang(){
    kalimat("menang");
    ketemu = true;
}

void menebak(){
    do {
        kalimat("tebak");
        if (percobaan >= 10){
            quitAble = true;
            kalimat("opsiQuit");
        }
        cin >> tebak;
        if (tebak == -1 && quitAble){
            kalimat("kalah");
            ketemu = true;
            break;
        }
        if (tebak == angkaRahasia){
            menang();
        }
        else if(tebak > batasAtas)
            kalimat("OBA");
        else if(tebak < batasBawah)
            kalimat("OBB");
        else if (tebak < angkaRahasia){
            kalimat("BB");
        }else if (tebak > angkaRahasia) {
            kalimat("BA");
        }else{
            cout << "Mohon hanya menginput angka ! \n\n";
        }
    } while (false);
}

void tanyaUlang(){
    do {
        cout << "Apakah anda ingin bermain lagi ? (y/t) :";
        cin >> cUlang;
        if (cUlang == 'y' || cUlang == 'Y'){
            bermain = true;
            break;
        }else if (cUlang == 't' || cUlang == 'T') {
            bermain = false;
            break;
        }else {
            cout << "Input 'y' untuk main lagi atau 't' untuk keluar.";
            cUlang = 'x';
        }
    } while (cUlang = 'x');
}

int main() {
    acak();
    bermain = true;

    // Loop Permainan
    while (bermain){
        inisialisasi();

        angkaRahasia = cariAngka(setting());
        kalimat("welcome");

        //Loop Ronde
        while (!ketemu){
            menebak();
        }
        tanyaUlang();
    }
}
