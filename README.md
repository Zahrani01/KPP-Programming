// NAMA		:AFCHRYSILLVA ZAHRANI WAHYUNIRMALA
// NRP		:5022221013
// Jurusan	:Teknik Elektro

#include <iostream>
#include <cmath>
using namespace std;

#define GRAVITASI 10 //10 m/s^2
#define START_PENGUKURAN 1 //pengukuran dimulai dari 1 meter
#define SUDUT 45 //sudut elevasi tembakan
#define PHI 3.14159625

float V0, loss, input, Vtangen;

int mencari_V0(int Vtangen, int loss)
{
    /* Tulis fungsi mencari v0 kalian disini */
    V0 = Vtangen - loss ;
    return V0;
}

int speed_dgn_loss(int Vtangen)
{
    /* tulis fungsi hitung_loss kalian disini */
    
    if(Vtangen <= 11 && Vtangen >= 2){
        loss = 1;
    
    } else if (Vtangen <= 23 && Vtangen >= 14) {
        loss = 3;
        
    } else if (Vtangen <= 30 && Vtangen >= 26 ) {
        loss = 5;

    } else {
        cout<< "Nilai tidak ditemukan"; 
    }
    return loss; 
    
}

int main() {
    /* tulis kode utama kalian disini */
    int jarak;
    float Vtangen = 30;
    
    speed_dgn_loss(Vtangen);
    mencari_V0(Vtangen, loss);
    
    //sesuai dengan persamaan jarak max yaitu (Vo^2 * sin2a)/g
    jarak = pow(V0,2) * sin(2*SUDUT*PHI/180) /GRAVITASI; 
    //perhitungan kecepatan tangensial didapat dari V0+loss yang kemudian V0 diisi dengan persamaan akar(jarak*g)/sin2a
    //sehingga
    Vtangen = sqrt(jarak*GRAVITASI/sin(2*SUDUT*PHI/180)) + loss; 
    
    
    cout << jarak << " " << Vtangen <<endl;
    
    return 0;
}
