# edelweiss
#include <cmath>
#include <iostream>
#include <string>
using namespace std;

struct element {
  string symbol, Name;
  int AtomicNum, AtomicMass;
};
 element arr[] = {
      {"H", "Hydrogen", 1, 1},
      {"He", "Helium", 2, 2},
      {"Li", "Lithium", 3, 7},
      {"Be", "Beryllium", 4, 9},
      {"B","Boron", 5, 11},
      // {"C","", ,},
      // {"N","", ,},
      // {"O","", ,},
      // {"F","", ,},
      // {"Ne","", ,},
      // {"Na","", ,},
  };

void AtomicCheck (int num){
  bool found = false;
  for (int i=1; i<25; i++){
      if (arr[i].AtomicNum == num){
        cout << "Elemental Symbol: " << arr[i].symbol << endl;
        cout << "Elemental Name: " << arr[i].Name << endl;
        cout << "Elemental Mass: " << arr[i].AtomicMass << endl;
        found = true;
      }
  }
  if (found == false){
      cout << "Please re-run the code and enter a valid Atomic Number!";
  }
}

void MassCheck (int num){
  bool found = false;
  for (int i=1; i<25; i++){
      if (arr[i].AtomicMass == num){
        cout << "Elemental Symbol: " << arr[i].symbol << endl;
        cout << "Elemental Name: " << arr[i].Name << endl;
        cout << "Elemental Atomic number: " << arr[i].AtomicNum << endl;
        found = true;
      }
  }
  if (found == false){
      cout << "Please re-run the code and enter a valid Mass Number!";
  }
}

void SymbolCheck (string txt){
  bool found = false;
  for (int i=1; i<25; i++){
      if (arr[i].symbol == txt){
        cout << "Elemental Name: " << arr[i].Name << endl;
        cout << "Elemental Atomic Mass: " << arr[i].AtomicMass << endl;
        cout << "Elemental Atomic number: " << arr[i].AtomicNum << endl;
        found = true;
      }
  }
  if (found == false){
      cout << "Please re-run the code and enter a Symbol!";
  }
}

int main() {
  // declare function
  float m, n, k, x1, x2, yield_percentage, mass_element, mass_element1,
      molarity, molality, mass_solute, volume_solution, mole_fraction,
      moles_solute, moles_solvent, mole_atom, dilution, initial_concentration,
      initial_volume, final_concentration, final_volume;
  int x, a, b;
  double atm, atm1, mass_1atm, Avo_number = 6.022e+23, one_mole;

  // displaying calculator choice
  cout << "           C-C++ Calculator         " << endl;
  cout << "====================================" << endl;
  cout << "(1) Find yield percentage "
       << endl; // for an equilibrium reaction with two reactants and two
                // products;
  cout << "(2) Find molarity" << endl;
  cout << "(3) Find mole fraction" << endl;
  cout << "(4) Find mole of compound" << endl;
  cout << "(5) Find mass of one molecule(particle)" << endl;
  cout << "(6) Find molality" << endl;
  cout << "(7) Find dilution" << endl;
  cout << "(8) Find molecular geometry" << endl;
  cout << "(9) Find Element Properties" << endl;
  cout << "====================================" << endl;
  cout << "Please enter your choice : ";
  cin >> x;
  cout << endl;

  // calculation
  switch (x) {
  case 1:
    cout << "Input experimental mass: ";
    cin >> m;
    cout << "Input molar mass of main product: ";
    cin >> n;
    cout << "Input mass of reactant 1 in grams: ";
    cin >> mass_element;
    cout << "Input mass of reactant 2 in grams: ";
    cin >> mass_element1;
    cout << "Input molar mass of reactant 1: ";
    cin >> atm;
    cout << "Input molar mass of reactant 2: ";
    cin >> atm1;
    cout << "Input coefficient of rectant 1 in the equation: ";
    cin >> a;
    cout << "Input coefficient of reactant 2 in the equation: ";
    cin >> b;
    cout << "Input Ke of the reaction: ";
    cin >> k;
    x1 = (k * ((mass_element / atm) + (mass_element1 / atm1)) +
          sqrt((k * ((mass_element / atm) + (mass_element1 / atm1))) *
                   (k * ((mass_element / atm) + (mass_element1 / atm1))) -
               (4 * (k - 1) * k * (mass_element / atm) *
                (mass_element1 / atm1)))) /
         (2 * (k - 1));
    x2 = (k * ((mass_element / atm) + (mass_element1 / atm1)) -
          sqrt((k * ((mass_element / atm) + (mass_element1 / atm1))) *
                   (k * ((mass_element / atm) + (mass_element1 / atm1))) -
               (4 * (k - 1) * k * (mass_element / atm) *
                (mass_element1 / atm1)))) /
         (2 * (k - 1));
    if (x1 > x2) {
      yield_percentage = (m * 100) / (x1 * n);
    } else {
      yield_percentage = (m * 100) / (x2 * n);
    }
    cout << endl << "====================================" << endl;
    cout << "Yield percentage = " << yield_percentage << "%" << endl;
    break;

  case 2:
    cout << "Input mass of solute in grams: ";
    cin >> mass_solute;
    cout << "Input molar mass of solute: ";
    cin >> atm;
    cout << "Input volume of solution in mL: ";
    cin >> volume_solution;
    molarity = ((mass_solute / atm) * 1000) / volume_solution;
    cout << endl << "====================================" << endl;
    cout << "Molarity = " << molarity << " M" << endl;
    break;

  case 3:
    cout << "Input moles of solute: ";
    cin >> moles_solute;
    cout << "Input moles of solvent: ";
    cin >> moles_solvent;
    mole_fraction = moles_solute / (moles_solute + moles_solvent);
    cout << endl << "====================================" << endl;
    cout << "Mole fraction = " << mole_fraction << endl;
    break;

  case 4:
    cout << "Input mass of element: ";
    cin >> mass_element;
    cout << "Input atomic mass of element in gram/mole: ";
    cin >> atm;
    one_mole = mass_element / atm;
    cout << endl << "====================================" << endl;
    cout << "Moles of compound = " << one_mole << " mol" << endl;
    break;

  case 5:
    cout << "Input molecular mass in gram/mole: ";
    cin >> atm;
    mass_1atm = atm / Avo_number;
    cout << endl << "====================================" << endl;
    cout << "Mass of one molecule(particle) = " << mass_1atm << " g" << endl;
    break;

  case 6:
    cout << "Input mass of solute in grams: ";
    cin >> mass_element;
    cout << "Input molecular mass of solute in grams/mole: ";
    cin >> atm;
    cout << "input mass of solvent in g: ";
    cin >> mass_element1;
    molality = ((mass_element / atm) * 1000) / mass_element1;
    cout << endl << "====================================" << endl;
    cout << "Molality = " << molality << " m" << endl;
    break;

  case 7:
    cout << "(1) Find Initial concentration " << endl;
    cout << "(2) Find initial volume" << endl;
    cout << "(3) Find final concentration" << endl;
    cout << "(4) Find final volume" << endl;
    cout << endl
         << "====================================" << endl
         << "Choose your option: " << endl;
    int y;
    cin >> y;

    if (y == 1) {
      cout << "Input initial volume in mL: ";
      cin >> initial_volume;
      cout << "Input final volume in mL: ";
      cin >> final_volume;
      cout << "Input final concentration: ";
      cin >> final_concentration;
      initial_concentration =
          (final_concentration * final_volume) / initial_volume;
      cout << endl
           << "====================================" << endl
           << "Initial concentration = " << initial_concentration << " M"
           << endl;
    }

    if (y == 2) {
      cout << "Input final concentration: ";
      cin >> final_concentration;
      cout << "Input final volume in mL: ";
      cin >> final_volume;
      cout << "Input initial concentration: ";
      cin >> initial_concentration;
      initial_volume =
          (final_concentration * final_volume) / initial_concentration;
      cout << endl
           << "====================================" << endl
           << "Initial volume = " << initial_volume << " mL" << endl;
    }

    if (y == 3) {
      cout << "Input initial concentration: ";
      cin >> initial_concentration;
      cout << "Input initial volume in mL: ";
      cin >> initial_volume;
      cout << "Input initial volume in mL: ";
      cin >> final_volume;
      final_concentration =
          (initial_concentration * initial_volume) / final_volume;
      cout << endl
           << "====================================" << endl
           << "Final concentration = " << final_concentration << " M" << endl;
    }

    if (y == 4) {
      cout << "Input initial concentration: ";
      cin >> initial_concentration;
      cout << "Input initial volume in mL: ";
      cin >> initial_volume;
      cout << "Input initial concentration: ";
      cin >> final_concentration;
      final_volume =
          (initial_concentration * initial_volume) / final_concentration;
      cout << endl
           << "====================================" << endl
           << "Final volume = " << final_volume << " mL" << endl;
    }
    break;

  case 8:
    int Bpairs = 0;
    int Lpairs = 0;
    cout << "Input number of bonding pairs: ";
    cin >> Bpairs;
    cout << "Input number of lone pairs: ";
    cin >> Lpairs;
    if ((Bpairs == 1 || Bpairs == 2) && Lpairs == 0) {
      cout << "Molecular shape : Linear" << endl;
      cout << "Possible angles : 180° only" << endl;
    }
    if ((Bpairs == 3) && Lpairs == 0) {
      cout << "Molecular shape : Trigonal Planar" << endl;
      cout << "Possible angles : 120° only" << endl;
    }
    if ((Bpairs == 4) && Lpairs == 0) {
      cout << "Molecular shape : Tetrahedral" << endl;
      cout << "Possible angles : 109.5° only" << endl;
    }
    if ((Bpairs == 5) && Lpairs == 0) {
      cout << "Molecular shape : Trigonal Bipyramidal" << endl;
      cout << "Possible angles : 120° and 90°" << endl;
    }
    if ((Bpairs == 6) && Lpairs == 0) {
      cout << "Molecular shape : Octahedral" << endl;
      cout << "Possible angles : 90° only" << endl;
    }
    if ((Bpairs == 2) && Lpairs == 1) {
      cout << "Molecular shape : Bent" << endl;
      cout << "Possible angles : 120° only" << endl;
    }
    if ((Bpairs == 3) && Lpairs == 1) {
      cout << "Molecular shape : Trigonal Pyramidal" << endl;
      cout << "Possible angles : 107° only" << endl;
    }
    if ((Bpairs == 4) && Lpairs == 1) {
      cout << "Molecular shape : Distorted tetrahedral" << endl;
      cout << "Possible angles : <90° and <120° " << endl;
    }
    if ((Bpairs == 5) && Lpairs == 1) {
      cout << "Molecular shape : Tetragonal pyramidal" << endl;
      cout << "Possible angles : <90°" << endl;
    }
    if ((Bpairs == 2) && Lpairs == 2) {
      cout << "Molecular shape : Bent" << endl;
      cout << "Possible angles : 106.5°" << endl;
    }
    if ((Bpairs == 3) && Lpairs == 2) {
      cout << "Molecular shape : T-Shaped" << endl;
      cout << "Possible angles : <90°" << endl;
    }
    if ((Bpairs == 4) && Lpairs == 2) {
      cout << "Molecular shape : Tetragonal planar" << endl;
      cout << "Possible angles : only 90°" << endl;
    }
    if ((Bpairs == 2) && Lpairs == 3) {
      cout << "Molecular shape : Linear" << endl;
      cout << "Possible angles : only 180°" << endl;
    }
    if ((Bpairs == 3) && Lpairs == 3) {
      cout << "Molecular shape : T-shaped" << endl;
      cout << "Possible angles : <90°" << endl;
    }
    if ((Bpairs == 2) && Lpairs == 4) {
      cout << "Molecular shape : Linear" << endl;
      cout << "Possible angles : only 180°" << endl;
    }
    break;

    case 9:
    cout << "(1) Given Atomic Number" << endl;
    cout << "(2) Given Element symbol" << endl;
    cout << "(3) Given Mass number" << endl;
    cout << "Choose your option: ";
    int r;
    cin r;
    if (r==1){
      cout << "Enter the Atomic Number: ";
      int q;
      cin >> q;
      AtomicCheck(q);
    }
    if (r==2){
      cout << "Enter the Element Symbol: ";
      string w;
      cin >> w;
      SymbolCheck(txt);
    }
    if (r==3){
      cout << "Enter the Mass Number; ";
      int e;
      cin >> e;
      MassCheck(e);
    }
    else{
      cout << "please enter valid option and re-run the program";
      break;
    }
    default:
      cout << "please run the code again and enter a valid option.";
      break;

    return 0;
  }
}
