// MODEL EXAM :
// 1. BINARY SEARCH - NO OF OCCURENCES :

#include<iostream>
using namespace std;
int main(){
    int n;
    cin>>n;
    int a[n];
    for(int i=0;i<n;i++){
        cin>>a[i];
    }
    int key;
    cin>>key;
    int first=0,last,mid;
    last=n-1;
    while(first<=last){
        mid=(first+last)/2;
        if(a[mid]<key){
            first=mid+1;
        }
        else if(a[mid]==key){
            cout<<mid;
            break;
        }
        else{
            last=mid-1;
        }
    }
    if(first>last){
        cout<<"NO OCCURRENCES";
    }
}

// 2. LINEAR SEARCH :

#include<iostream>
using namespace std;
int main(){
    int n,f=0;
    cin>>n;
    int arr[n];
    for(int i=0;i<n;i++){
        cin>>arr[i];
    }
    int num;
    cin>>num;
    for(int i=0;i<n;i++){
        if(num==arr[i]){
            f++;
            break;
        }
    }
    if(f==0){
        cout<<"No";
        // cout<<num<<" is not present";
    }
    else{
        cout<<"Yes";
        // cout<<num<<" is present";
    }
}

// 3. BUBBLE SORT:

#include<iostream>
using namespace std;
void bubble(int arr[],int n){
    for(int i=0;i<n;i++){
        for(int j=i+1;j<n;j++){
            if(arr[i] > arr[j]){
                int temp=arr[i];
                arr[i]=arr[j];
                arr[j]=temp;
            }
        }
    }
}
int main(){
    int n;
    cin>>n;
    int arr[n];
    for(int i=0;i<n;i++){
        cin>>arr[i];
    }
    bubble(arr,n);
    for(int i=0;i<n;i++)
    cout<<arr[i]<<" ";
}

// 4. INSERTION SORT ALGORITHM:

#include<iostream>
using namespace std;
void insert(int arr[],int n){
    for(int i=1;i<n;i++){
        int key=arr[i];
        int j=i-1;
        for(;j>=0 && arr[j]>key;j--){
            arr[j+1]=arr[j];
        }
        arr[j+1]=key;
    }
}
int main(){
    int n;
    cin>>n;
    int arr[n];
    for(int i=0;i<n;i++){
        cin>>arr[i];
    }
    insert(arr,n);
    for(int i=0;i<n;i++)
    cout<<arr[i]<<" ";
}

// 5. SHYAM - SELECTION SORT QUESTION:

#include<iostream> 
using namespace std;
int main(){
    int n,d,m,y;
    cin>>n;
    int ar[n];
    for(int i=0;i<n;i++){
        cin>>d>>m>>y;
        ar[i] = (y*10000) + (m*100) + (d);
    }
    for(int i=0;i<n-1;i++){
        int mini = i;
        for(int j=i+1;j<n;j++){
            if(ar[j]<ar[mini])
            mini = j;
        }
        if(mini!=i)
        swap(ar[i],ar[mini]);
    }
    for(int i=0;i<n;i++){
        cout<<ar[i]%100<<" ";
        ar[i]/=100;
        cout<<ar[i]%100<<" ";
        ar[i]/=100;
        cout<<ar[i]<<"\n";
    }
}

// 6. HEAP SORT:

#include<iostream>
using namespace std;
int heap(int arr[],int n,int i){
    int l=i;
    int left=2*i+1;
    int right=2*i+2;
    if(left < n && arr[left] > arr[l]){
        l=left;
    }
    if(right < n && arr[right] > arr[l]){
        l=right;
    }
    if(l!=i){
        swap(arr[i],arr[l]);
        heap(arr,n,l);
    }
}
int main(){
    int n;
    cin>>n;
    int arr[n];
    for(int i=0;i<n;i++){
        cin>>arr[i];
    }
    for(int i=(n/2)-1;i>=0;i--){
        heap(arr,n,i);
    }
    for(int i=n-1;i>=0;i--){
        swap(arr[i],arr[0]);
        heap(arr,i,0);
    }
    for(int i=0;i<n;i++){
        cout<<arr[i]<<" ";
    }
}

// 7. QUICK SORT:

#include<iostream>
using namespace std;
int partition(int arr[],int low,int high){
    int pivot = arr[low];
    int i=low,j=high;
    while(i<=j){
        while(arr[i] <= pivot)
        i++;
        while(arr[j] > pivot)
        j--;
        if(i<j)
        swap(arr[i],arr[j]);
    }
    swap(arr[low],arr[j]);
    return j;
}
void quicksort(int arr[],int low,int high){
    if(low<=high){
        int j=partition(arr,low,high);
        quicksort(arr,low,j-1);
        quicksort(arr,j+1,high);
    }
}
int main(){
    int n;cin>>n;
    int arr[n],i;
    for(i=0;i<n;i++)
    cin>>arr[i];
    quicksort(arr,0,n-1);
    for(i=0;i<n;i++)
    cout<<arr[i]<<" ";
}

// 8. MERGE SORT :

#include<iostream>
using namespace std;
void merge(int arr[],int low,int mid,int high){
    int i=low,j=mid+1,k=low,s=high;
    int m[s];
    while(i <= mid && j<= high){
        if(arr[i]<arr[j])
            m[k++] = arr[i++];
        else
            m[k++] = arr[j++];
    }
    while(i<=mid)
        m[k++] = arr[i++];
    while(j<=high)
        m[k++] = arr[j++];
        
    for(i=low;i<=high;i++)
        arr[i] = m[i];
}
int msort(int arr[],int low,int high){
    if(low<high){
        int mid=(low+high)/2;
        msort(arr,low,mid);
        msort(arr,mid+1,high);
        merge(arr,low,mid,high);
    }
}
int main(){
    int n;cin>>n;
    int arr[n],i;
    for(i=0;i<n;i++)
        cin>>arr[i];
    msort(arr,0,n-1);
    for(i=0;i<n;i++)
        cout<<arr[i]<<" ";
}

// 9. ACTIVITY SELECTION :

#include<iostream>
using namespace std;
struct dem{
    string n;
    int m;
    int o;
};
int main(){
    int n;
    cin>>n;
    struct dem arr[n];
    for(int i=0;i<n;i++){
        cin>>arr[i].n>>arr[i].m>>arr[i].o;
    }
    for(int i=0;i<n;i++){
        for(int j=i+1;j<n;j++){
            if(arr[i].o > arr[j].o){
                swap(arr[i],arr[j]);
            }
        }
    }
    int temp=0;
    cout<<"Selected Activities are: "<<"\n"<<arr[0].n<<" ";
    for(int i=1;i<n;i++){
        if(arr[i].m >= arr[temp].o){
            cout<<arr[i].n<<" ";
            temp=i;
        }
    }
}

// 10. KNAPSACK PROBLEM :

#include<iostream>
#include<iomanip>
using namespace std;
struct knap{
    float w;
    float p;
    float pr;
};
int main(){
    int n,c;
    cin>>n;
    struct knap arr[n];
    for(int i=0;i<n;i++){
        cin>>arr[i].w>>arr[i].p;
        arr[i].pr=(arr[i].p/arr[i].w);
    }
    cin>>c;
    for(int i=0;i<n;i++){
        for(int j=i+1;j<n;j++){
            if(arr[i].pr < arr[j].pr){
                swap(arr[i],arr[j]);
            }
        }
    }
    float max=0;
    cout<<"Maximum profit is:- ";
    for(int i=0;i<n;i++){
        if(c>=arr[i].w){
           c-=arr[i].w;
           max+=(arr[i].pr * arr[i].w);
        }
        else{
            max+=(c * arr[i].pr);
            break;
        }
    }
    cout<<fixed<<setprecision(2)<<max;
}

// 11. NAIVE ALGORITHM - FIND OCCURENCE OF SUBSTRING:

#include<iostream>
#include<cstring>
using namespace std;
int search(char pat[],char txt[]){
    int m=strlen(pat);
    int n=strlen(txt);
    for(int i=0;i<=n-m;i++){
        int j;
        for(j=0;j<m;j++){
            if(txt[i+j]!=pat[j]){
                break;
            }
        }
        if(j==m){
            return i;
        }
    }
    return -1;
}
int main(){
    char txt[100];
    char pat[100];
    cin>>txt>>pat;
    int r=search(pat,txt);
    if(r!=-1){
        cout<<"Found at "<<r;
    }
    else{
        cout<<"Not Found";
    }
}

// 12. KMP ALGORITHM :

#include <iostream>
#include<cstring>
using namespace std;
void KMP(char text[], char pattern[]){
    int m = strlen(text);
    int n = strlen(pattern);
    int f=0;
    int next[n + 1];
    for (int i = 0; i < n + 1; i++){
        next[i] = 0;
    }
    for (int i = 1; i < n; i++){
        int j = next[i];
        while (j > 0 && pattern[j] != pattern[i]){
            j = next[j];
        }
        if (j > 0 || pattern[j] == pattern[i]){
            next[i + 1] = j + 1;
        }
    }
    for (int i = 0, j = 0; i < m; i++){
        if (text[i] == pattern[j]){
            if (++j == n) {
                cout << "Found at " << i - j + 1 << endl;
                f=1;
            }
        }
        else if (j > 0){
            j = next[j];
            i--;
        }
    }
    if(f==0)
    cout<<"Not Found";
}
int main(){
    char text[100] ;
    char pattern[100] ;
    cin>>text;
    cin>>pattern;
    KMP(text, pattern);
}

// 13. SUBSET SUM :

#include<iostream>
using namespace std;
static int sc=0;
void subsum(int list[], int sum,int start,int target_sum ,int n){
    if(target_sum==sum){
        sc++;
        if(start<n)
        subsum(list,sum-list[start-1],start,target_sum,n);
    }
    else{
        for(int i=start;i<n;i++){
            subsum(list,sum+list[i],i+1,target_sum,n);
        }
    }
}
int main(){
    int n;
    cin>>n;
    int a[n];
    for(int i=0;i<n;i++){
        cin>>a[i];
    }
    int s;cin>>s;
    subsum(a,0,0,s,n);
    cout<<sc;
}

// 14. RAT IN MAZE :

// You are using GCC
#include<iostream>
using namespace std;
bool issafe(int** arr, int x, int y, int n){
    if(x<n && y<n && arr[x][y]==1){
        return true;
    }
    return false;
}
bool ratinMaze(int** arr, int x, int y, int n, int** solArr){
    if(x==n-1 && y==n-1){
        solArr[x][y]=1;
        return true;
    }
    if(issafe(arr, x, y, n)){
        solArr[x][y]=1;
        if(ratinMaze(arr, x+1, y, n, solArr)){
            return true;
        }
        if(ratinMaze(arr, x, y+1, n, solArr)){
            return true;
        }
        solArr[x][y]=0;
        return false;
    }
    return false;
}
int main(){
    int n;
    cin>>n;
    int** arr=new int*[n];
    for(int i=0; i<n; i++){
        arr[i]=new int[n];
    }
    for(int i=0; i<n; i++){
        for(int j=0; j<n; j++){
            cin>>arr[i][j];
        }
    }
    int** solArr=new int*[n];
    for(int i=0; i<n; i++){
        solArr[i] = new int[n];
        for(int j=0; j<n; j++){
            solArr[i][j]=0;
        }
    }
    if(ratinMaze(arr, 0, 0, n, solArr)){
        for(int i=0; i<n; i++){
        for(int j=0; j<n; j++){
            cout<<solArr[i][j]<<" ";
        }cout<<endl;

        }
    }
    else{
        cout<<"Solution doesn't exist";
    }
}

// 15. LONGEST COMMON SUBSEQUENCE :

#include<iostream>
#include<algorithm>
using namespace std;
int max(int a,int b){
    if(a>b){
        return a;
    }
    return b;
}
int main(){
    string x,y;
    cin>>x>>y;
    int n=x.length();
    int m=y.length();
    int a[n+1][m+1];
    int maxi=0;
    for(int i=0;i<n+1;i++){
        for(int j=0;j<m+1;j++){
            if(i==0 || j==0){
                a[i][j]=0;
            }
            else if(y[j-1]==x[i-1]){
                a[i][j]=a[i-1][j-1]+1;
                if(a[i][j]>maxi){
                    maxi=a[i][j];
                }
            }
            else{
                a[i][j]=max(a[i-1][j],a[i][j-1]);
            }
        }
    }
    cout<<maxi;
}

// 16. LEVENSHTEIN DISTANCE :

#include<iostream>
using namespace std;
int min(int a,int b,int c){
    if(a<b && a<c){
        return a;
    }
    else if(b<c){
        return b;
    }
    return c;
}
int kpo(char a,char b){
    if(a==b){
        return 0;
    }
    return 1;
}
int main(){
    string x,y;
    cin>>x>>y;
    int m=x.length();
    int n=y.length();
    int a[m+1][n+1];
    for(int i=0;i<=m;i++){
        for(int j=0;j<=n;j++){
            if(i==0){
                a[i][j]=j;
            }
            else if(j==0){
                a[i][j]=i;
            }
            else{
                a[i][j]=min((a[i-1][j-1]+kpo(y[j-1],x[i-1])),a[i-1][j]+1,a[i][j-1]+1);
            }
        }
    }
    cout<<a[m][n];
}

// 17. SEGMENT TREE RANGE MINIMUM QUERY :

#include<iostream>
#include<cmath>
using namespace std;
int cr(int a[],int *st,int x,int y,int i){
    if(x==y){
        return a[x];
    }
    int mid=(x+y)/2;
    st[i]=min(cr(a,st,x,mid,2*i+1),cr(a,st,mid+1,y,2*i+2));
}
int *create(int a[],int x,int b){
    int n=b-x+1;
    int y=(int)(ceil(log2(n)));
    int ma=2*(int)pow(2,y)-1;
    int *st=new int[ma];
    cr(a,st,x,b,0);
    return st;
}
int main(){
    int n;
    cin>>n;
    int a[n];
    for(int i=0;i<n;i++){
        cin>>a[i];
    }
    int x,y;
    cin>>x>>y;
    int *st=create(a,x,y);
    cout<<"Minimum of values in range ["<<x<<", "<<y<<"] is = "<<st[0];
}

// 18. RANGE MINIMUM QUERY USING SPARSE TABLE :

#include<iostream>
#include<cmath>
using namespace std;
#define kp 100
int main(){
    int a[kp][kp];
    int n;
    cin>>n;
    int m[n];
    for(int i=0;i<n;i++){
        cin>>m[i];
    }
    for(int i=0;i<n;i++){
        a[i][0]=m[i];
    }
    for(int j=1;(1<<j)<=n;j++){
        for(int i=0;(i+(1<<j)-1)<n;i++){
            if(a[i][j-1]<a[i+(1<<(j-1))][j-1]){
                a[i][j]=a[i][j-1];
            }
            else{
                a[i][j]=a[i+(1<<(j-1))][j-1];
            }
        }
    }
    int l,r;
    cin>>l>>r;
    int j=(int)log2(r-l+1);
    if(a[l][j]<=a[r-(1<<j)+1][j]){
        cout<<a[l][j];
    }
    else{
        cout<<a[r+(1<<j)+1][j];
    }
}

// 19. FLOYD WARSHALL ALGORITHM :

#include<iostream>
using namespace std;
int main(){
    int n;
    cin>>n;
    int a[n][n];
    for(int i=0;i<n;i++){
        for(int j=0;j<n;j++){
            a[i][j]=0;;
        }
    }
    int v,x,y,z;
    cin>>v;
    for(int i=0;i<v;i++){
        cin>>x>>y>>z;
        a[x][y]=z;
        a[y][x]=z;
    }
    cout<<"Original matrix"<<endl;
    for(int i=0;i<n;i++){
        for(int j=0;j<n;j++){
            if(i!=j&&a[i][j]==0){
                a[i][j]=999;
                cout<<"INF"<<" ";
                
            }
            else{
                cout<<a[i][j]<<" ";
            }
        }
        cout<<endl;
    }
    // cout<<endl;
    cout<<"Shortest path matrix"<<endl;
    for(int k=0;k<n;k++){
        for(int i=0;i<n;i++){
            for(int j=0;j<n;j++){
                if(a[i][j]>a[i][k]+a[k][j]){
                    a[i][j]=a[i][k]+a[k][j];
                }
            }
        }
    }
    for(int i=0;i<n;i++){
        for(int j=0;j<n;j++){
            cout<<a[i][j]<<" ";
        }
        cout<<endl;
    }
}

// 20. PRIMS ALGORITHM :

#include<iostream>
using namespace std;
#define m 100
void print(int p[],int n,int a[m][m]){
    for(int i=1;i<n;i++){
        cout<<p[i]<<" "<<i<<" "<<a[i][p[i]]<<endl;
    }
}
int minl(int a[m][m],bool ta[],int mi[],int n){
    int mt=1000,in;
    for(int i=0;i<n;i++){
        if(!ta[i]&&mi[i]<mt){       
            mt=mi[i];
            in=i;
        }
    }
    return in;
}
void prims(int a[m][m],int n){
    int pa[n],mi[n];
    bool ta[n];
    for(int i=0;i<n;i++){
        mi[i]=999;ta[i]==false;
    }
    mi[0]=0;
    pa[0]=-1;
    for(int cou=0;cou<n-1;cou++){
        int u=minl(a,ta,mi,n);
        ta[u]=true;
        for(int i=0;i<n;i++){
            if(!ta[i]&&a[u][i]&&a[u][i]<mi[i]){
                pa[i]=u;
                mi[i]=a[u][i];
            }
        }
    }
    print(pa,n,a);
}
int main(){
    int n;
    cin>>n;
    int a[m][m];
    for(int i=0;i<n;i++){
        for(int j=0;j<n;j++){
            cin>>a[i][j];
        }
    }
    prims(a,n);
}

// 21. DIJKSTRA'S ALGORITHM :

#include<iostream>
using namespace std;
#define n 5
void print(int min[]){
    cout<<"Vertex"<<"\t\t\t"<<"Distance from Source"<<endl;
    for(int i=0;i<n;i++){
        cout<<i<<"\t\t\t"<<min[i]<<endl;
    }
}
int mi(int a[n][n],int c,int min[],bool ta[]){
    int m=1000,in;
    for(int i=0;i<n;i++){
        if(!ta[i]&&min[i]<= m){
            m=min[i];
            in =i;
        }
    }
    return in;
}
void dij(int a[n][n],int s){
    int min[n];
    bool ta[n];
    for(int i=0;i<n;i++){
        min[i]=999;
        ta[i]=0;
    }
    min[s]=0;
    for(int cou=0;cou<n-1;cou++){
        int u=mi(a,cou,min,ta);
        ta[u]=true;
        for(int i=0;i<n;i++){
            if(a[u][i]&&!ta[i]&&min[u]!=999&&min[u]+a[u][i]<min[i]){
                min[i]=min[u]+a[u][i];
            }
        }
    }
    print(min);
}
int main(){
    int a[n][n];
    for(int i=0;i<n;i++){
        for(int j=0;j<n;j++){
            cin>>a[i][j];
        }
    }
    int s;
    cin>>s;
    dij(a,s);
}

// 22. KRUSKAL'S ALGORITHM:

#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;
struct Edge {
    int u, v, weight;
};
class DisjointSet {
public:
    vector<int> parent;
    DisjointSet(int n) {
        parent.resize(n);
        for (int i = 0; i < n; i++) {
            parent[i] = i;
        }
    }
    int find(int node) {
        if (parent[node] == node) return node;
        return parent[node] = find(parent[node]);
    }
    void unionSets(int u, int v) {
        int rootU = find(u);
        int rootV = find(v);
        parent[rootU] = rootV;
    }
};
void kruskal(int vertices, vector<Edge>& edges) {
    sort(edges.begin(), edges.end(), [](const Edge& a, const Edge& b) {
        return a.weight < b.weight;
    });
    DisjointSet disjointSet(vertices);
    vector<Edge> minimumSpanningTree;
    int totalCost = 0;
    for (Edge edge : edges) {
        if (disjointSet.find(edge.u) != disjointSet.find(edge.v)) {
            minimumSpanningTree.push_back(edge);
            totalCost += edge.weight;
            disjointSet.unionSets(edge.u, edge.v);
        }
    }
    cout << "Following are the edges in the constructed MST" << endl;
    for (Edge edge : minimumSpanningTree) {
        cout << edge.u << " -- " << edge.v << " == " << edge.weight << endl;
    }
    cout << "Minimum Cost Spanning Tree: " << totalCost << endl;
}
int main() {
    int vertices, edgesCount;
    cin >> vertices >> edgesCount;
    vector<Edge> edges(edgesCount);
    for (int i = 0; i < edgesCount; i++) {
        cin >> edges[i].u >> edges[i].v >> edges[i].weight;
    }
    kruskal(vertices, edges);
}
