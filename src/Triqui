#include <iostream>
using namespace std;

void estTabla(char a[3][3]){
    cout << "\nTablero actual:\n";
    for (int F = 0; F < 3; F++) {
        for (int C = 0; C < 3; C++) {
            cout << a[F][C] << " ";
            if(C==0||C==1){cout<<"| ";}
        }
    if(F==0||F==1){cout<<"\n---------";}
    cout << endl;
    }
}
int ingCasilla(char turno){
    int n;
    cout << "\nTurno del jugador " << turno << endl;
    cout << "La casilla a seleccionar: "; cin >> n;
    return n;
}

bool verificarError(char a[3][3], int n, char turno, int jugadas){
    if (cin.fail()) {
        cout << "Movimiento invalido, intenta otra vez.\n";
        cin.clear();
        cin.ignore(10000, '\n');
        return false;
    }
    if(n<1||n>9){
        cout << "Movimiento invalido, intenta otra vez.\n";
        return false;
    }
    if (a[(n-1)/3][(n-1)%3]=='X'||a[(n-1)/3][(n-1)%3]=='O') {
        cout << "Movimiento invalido, intenta otra vez.\n";
        return false;
    }
    return true;
    
}

void estadJuego(char a[3][3],char turno,int n, int &jugadas){
    a[(n-1)/3][(n-1)%3] = turno;
    jugadas++;
}

bool verificarVictoria(char a[3][3], char turno, int jugadas){
    for (int i = 0; i < 3; i++) {
        if (a[i][0] == turno && a[i][1] == turno && a[i][2] == turno) {
            cout << "\nGanó el jugador(-) " << turno << endl;
            return false;
        }
        if (a[0][i] == turno && a[1][i] == turno && a[2][i] == turno) {
            cout << "\nGanó el jugador(|) " << turno << endl;
            return false;
            
        }
    }
    if (a[0][0] == turno && a[1][1] == turno && a[2][2] == turno) {
        cout << "\nGanó el jugador(\\) " << turno << endl;
        return false;
    }
    if (a[0][2] == turno && a[1][1] == turno && a[2][0] == turno) {
        cout << "\nGanó el jugador(/) " << turno << endl;
        return false;
    }
    if (jugadas == 9) {
            cout << "\nEmpate!\n";
        return false;
    }
    return true;
}
char cambioTurno(char turno){
    turno = (turno == 'X') ? 'O' : 'X';
    return turno;
}
char reiniciarPartida(char &r, char a[3][3], char &turno, int &jugadas){
    cout<<"¿Deseas reiniciar la partidad? Si(1), No(cualquier otro valor) "; cin >> r;
    if(r=='1'){
        turno='X';
        jugadas=0;
        char num = '1';
        for(int i = 0; i < 3; i++){
            for(int j = 0; j < 3; j++){
                a[i][j] = num++;
            }
        }
        
    }
    return r;
}
void run(){
    char a[3][3]={
    {'1','2','3'},
    {'4','5','6'},
    {'7','8','9'}};
    int n;
    int jugadas = 0;
    char turno = 'X';
    char r='1';
    while(r=='1'){
        estTabla(a);
        while(true){
            n = ingCasilla(turno);
            if(!verificarError(a,n,turno,jugadas)){continue;}
            estadJuego(a,turno,n, jugadas);
            estTabla(a);
            if(!verificarVictoria(a, turno, jugadas)){break;}
            turno = cambioTurno(turno);
        }
        r = reiniciarPartida(r, a, turno, jugadas);
    }
}
int main(){
    run();
    return 0;
}
