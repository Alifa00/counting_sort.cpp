```
#include <iostream>
#include <sstream>
#include <utility>

using namespace std;


void sqr_count_sort(double * vec, unsigned int len,double * result_vec);

static string error_message = "An error has occured while reading input data\n";

int
main ()
{
    unsigned int size;
    if( cin >> size ) {
        double * elements = new double[ size ];
        double * result = new double[ size ];
        
      //  cin.ignore( std::numeric_limits<streamsize>::max(), '\n' );
        cin.get();
        string line;
        if( getline( cin, line ) ) {
            istringstream stream( line );
            bool success = true;
            for( unsigned int i = 0; i < size; ++i ) {
                if ( !( stream >> elements[ i ] ) ) {
                    success = false;
                    break;
                }
            }
            success &= stream.eof();
            
            if( success ) {
        //void count_sort(double * vec, unsigned int len, int min, int max)
                sqr_count_sort( elements, size, result);
                for( unsigned int i = 0; i < size; ++i ) {
                    cout << result[ i ] << " ";
                }
            }
            else {
                cerr << error_message;
            }
        }
        
        delete [] result;
        delete [] elements;

    }
    else {
        cerr << error_message;
    }
    
    return 0;
}

```/*void count_sort(double * vec, unsigned int len, int min, int max)

{

	//assert(min <= max);
	//assert(vec != NULL);


	int * cnt = new int[max-min+1];


	for (int i = min; i <= max; ++i) {

		cnt[i - min] = 0;

	}


	for (int i = 0; i < len; ++i) {

		++cnt[vec[i] - min];

	}


	for (int i = min; i <= max; ++i) {

		for(int j = cnt[i - min]; j--;) {

			*vec++ = i;

		}

	}

	delete [] cnt;

}*/
```


void sqr_count_sort(double * vec, unsigned int len, double * result_vec){
    
    for (int  i = 0 ; i< len; i++){
        int c = 0;
	 for (int j = 0 ; j< i; j++ ){
            if (vec[j] <= vec[i]) c ++;
	 }
	for ( int j = i + 1 ;j < len; j++){
		if (vec[j] < vec[i] ) c++;
	}
	result_vec[c] = vec[i];

	}
}
```
