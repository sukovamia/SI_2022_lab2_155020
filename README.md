# Втора лабораториска вежба по Софтверско инженерство
Миа Шукова 155020

# Control Flow Graph
![graph](https://user-images.githubusercontent.com/100201351/173931708-feb6132a-e4b0-4ae6-a01d-b794cb78d160.png)

public static List<String> function(List<String> list) {
    if (list.size() <= 0) {                                                                                                                //1
        throw new IllegalArgumentException("List length should be greater than 0");                                                        //2
    }   
    int n = list.size();                                                                                                                   //3
    int rootOfN = (int) Math.sqrt(n);                                                                                                      //4
    if (rootOfN * rootOfN  != n) {                                                                                                         //5
        throw new IllegalArgumentException("List length should be a perfect square");          }                                           //6
    List<String> numMines = new ArrayList<>();                                                                                             //7                   
    for (int i = 0; i < n; i++) {                                                                                                          //8
        if (!list.get(i).equals("#")) {                                                                                                    //9
            int num = 0;                                                                                                                   //10
            if ( (i % rootOfN != 0 && list.get(i - 1).equals("#")) || (i % rootOfN != rootOfN - 1 && list.get(i + 1).equals("#")) ) {      //11
                if ( (i % rootOfN != 0 && list.get(i - 1).equals("#")) && (i % rootOfN != rootOfN - 1 && list.get(i + 1).equals("#")) ){   //12
                    num += 2;                                                                                                              //13
                }
                else {                                                                                                                     //14
                    num  += 1;                                                                                                             //15
                }
            }
            if (i - rootOfN >= 0 && list.get(i - rootOfN).equals("#")){                                                                    //16
                num++;                                                                                                                     //17
            }
            if (i + rootOfN < n && list.get(i + rootOfN).equals("#")){							                   //18
                num++;                                                                                                                     //19
            }
            numMines.add(String.valueOf(num));                                                                                             //20
        }
        else {                                                                                                                             //21
            numMines.add(list.get(i));                                                                                                     //22
        }
    }
    return numMines;                                                                                                                       //23
}

# Цикломатска комплексност

Цикломатска комплексност на кодот изнесува 8 и пресметана е преку формулата CYC = E – N + 2. 
Во овој случај: CYC = 26 - 20 + 2 = 8. Буквата Е го означува бројот на рабовите, а буквата N бројот на јазли во графот.                                
