# romano


#include <iostream>

using namespace std;

class numero_romano
{
private:
string numero;

public:
numero_romano() {}
numero_romano(string novo): numero(novo) { normalizar(); }

string valor() const { return numero; }
void novo_valor(string novo) { numero = novo; normalizar(); }

int para_arabe();

void normalizar();
};

int numero_romano::para_arabe()
{
int i, res = 0;

for(i=0; i<numero.size(); i++)
{
	switch(numero[i])
	{
		case 'I':
			if(numero[i+1] == 'V')
			{
				res += 4;
				i++;
			}
			else if(numero[i+1] == 'X')
			{
				res += 9;
				i++;
			}
			else
				res += 1;
		break;

		case 'X':
			if(numero[i+1] == 'L')
			{
				res += 40;
				i++;
			}
			else if(numero[i+1] == 'C')
			{
				res += 90;
				i++;
			}
			else
				res += 10;
		break;

		case 'C':
			if(numero[i+1] == 'D')
			{
				res += 400;
				i++;
			}
			else if(numero[i+1] == 'M')
			{
				res += 900;
				i++;
			}
			else
				res += 100;
		break;

		case 'M':
			res += 1000;
			break;

		case 'V': res += 5; break;
		case 'L': res += 50; break;
		case 'D': res += 500; break;
	}
}

return res;
}

void numero_romano::normalizar()
{
for(int i=0; i<numero.size(); i++)
{
	if(numero[i] == 'i') numero[i] = 'I';
	if(numero[i] == 'v') numero[i] = 'V';
	if(numero[i] == 'x') numero[i] = 'X';
	if(numero[i] == 'l') numero[i] = 'L';
	if(numero[i] == 'c') numero[i] = 'C';
	if(numero[i] == 'd') numero[i] = 'D';
	if(numero[i] == 'm') numero[i] = 'M';
}
}

class numero_arabe
{
private:
int numero;

public:
numero_arabe() {}
numero_arabe(int novo): numero(novo) {}

int valor() const { return numero; }
void novo_valor(int novo) { numero = novo; }	

string para_romano();
};

string numero_arabe::para_romano()
{
int i;
string res;

while(numero > 0)
{
	if(numero >= 1000)
	{
		res += "M";
		numero -= 1000;
	}
	else if(numero >= 100)
	{
		if(numero >= 900 && numero <= 999)
		{
			res += "CM";
			numero -= 900;
		}
		else if(numero >= 400 && numero <= 499)
		{
			res += "CD";
			numero -= 400;
		}
		else if(numero >= 500)
		{
			res += "D";
			numero -= 500;
		}
		else
		{
			res += "C";
			numero -= 100;
		}
	}
	else if(numero >= 10)
	{
		if(numero >= 90 && numero <= 99)
		{
			res += "XC";
			numero -= 90;
		}
		else if(numero >= 40 && numero <= 49)
		{
			res += "XL";
			numero -= 40;
		}
		else if(numero >= 50)
		{
			res += "L";
			numero -= 50;
		}
		else
		{
			res += "X";
			numero -= 10;
		}
	}
	else if(numero >= 1)
	{
		if(numero >= 9 && numero <= 9)
		{
			res += "IX";
			numero -= 9;
		}
		else if(numero >= 4 && numero <= 4)
		{
			res += "IV";
			numero -= 4;
		}
		else if(numero >= 5)
		{
			res += "V";
			numero -= 5;
		}
		else
		{
			res += "I";
			numero -= 1;
		}
	}
}

return res;
}

int main(int argc, char *argv[])
{
//De arabe para romano
//int num_arabe;
//string res_romano;

//cout << "Arabe: ";
//cin >> num_arabe;
//numero_arabe arabe(num_arabe);
//res_romano = arabe.para_romano();
//cout << endl << res_romano << endl;

//De romano para arabe	
string num_romano;
int res_arabe;

cout << "romano: ";
cin >> num_romano;
numero_romano romano(num_romano);
res_arabe = romano.para_arabe();
cout << endl << res_arabe << endl;

//----
return 0;
}
