# Boate-a-maux
ici repose des heures perdus

la je vais expliquer les différentes parties du code source, j'ai utilisé Visual Studio et pas de l'assembleur 
#masomaispassuicidaire
et je n'utilise pas de librairie externe, si vous avez pas windows en système d'éxploitation ou votre processeur est un processeur 32 bits, 
vous avez le source code, compilez-le vous-même. 

la y'a les librairie de base.

#include <iostream>   * input/output oublié, il est inutile
#include <fstream>    * lecture du fichier text des mots
#include <string>     * pour les mots, les mots 
#include <Windows.h>  * pour l'affichage en utf8 car sinon au revoirs les é et è
#include <list>       * pour les array list car les array de string c'est AUUUGGGGHHHHHH

using namespace std;  * vous comptez faire quoi sans accèder au system?

en bas la y'a les variable, voilà quoi.

fstream lesMots;      * import du fichier .txt 
string mots;          * je crois que c'est pour stocker les mots quelque parts bof
list<string> Lsmots;  * la liste des mots qui est inisialisé plus bas
string selected;      * un deuxième tampon
list<int> allIndeks;  * un truc pour le debbugage
int indeks;           * un troisième tampon lol, pour indexer 
int LsmotsLEN = 0;    * la longueur de la list des mots

la y'a une fonction pour obtenir un élements de la liste car le pd de scandinave qui a créé le c++, il a tous optimisé à 
mort mais faire une librairie standard complète c'est trop, les mecs de java ils sont moqué alors que leur libraire 
standard est ouf mais c'est pas très rapide, alors que python c'est plus lent que java.

string get(list<string> ltoget,int index){
    int* indexx= new int;
   *indexx=0;
    for (string stoget : ltoget) {
        if (index == *indexx) {
            return stoget;
        }
       *indexx+= 1;
    }
}

la fonction main, la base du programme quoi.

int main()
{
    time_t temp = time(0);     * c'est inutile ça, oubliez.
    SetConsoleOutputCP(65001); * pour mettre la console en utf-8.
    lesMots.open("mots.txt");  * charger le fichier .txt ,obtenir les mots.
    while (getline(lesMots, mots)) {  * lecture de chaque ligne, la ligne est placé dans la variable "mots".
        std::cout << mots << endl;    * affiche "mots".
        Lsmots.push_back(mots);       * ajoute "mots" à "Lsmots"
        LsmotsLEN++;                  * ajoute 1 a "LsmotsLEN++"
    }                                 * fin de la paranthèse lol xd ptdr hihihihaw
    for (string moti : Lsmots) {    * je raffiche les mots de la liste avec une boucle
        std::cout << moti << endl;  * afficher moti, la variable locale qui est ... ... ayant engendré la création d'Erebor.
    }                               * la boucle est boucle mdr xptdr
    while (!Lsmots.empty()) {                       * la boucle principale tant que la liste n'est pas vide
        system("cls");                              * je nettoie le cmd
        std::cout << endl;                          * le passe une ligne
        std::cout << "le mots est tiré:" << endl;   * affiche "le mot tiré est:", je suis teubé, j'ai inversé les mots
        indeks = (rand() + time(0)) % LsmotsLEN;    * indeks est l'index d'un mot de la liste aléatoire
        allIndeks.push_back(indeks);                * ajoute indeks à la liste "allIndeks", c'est pour le debbug, oubliez
        selected = get(Lsmots, indeks);             * selected est le mots de la liste à l'index numéros "indeks"
        std::cout << selected << endl;              * affiche "selected"
        Lsmots.remove(selected);                    * enlève selected de la liste
        LsmotsLEN--;                                * diminue de un la variable égale à longueur de la liste
        if (!Lsmots.empty()) {                       * une condition qui sert à R, mais condinception
            system("pause");                         * attend une réaction de l'utilisateur
        }                                            * fin de la condition
    }                                               * double fin xd
    std::cout << " tu a tiré tous les mots, relance le programme dans le cmd pour recommencer"; * le message de fin lol
}
