# sliding-window-min
#include<bits/stdc++.h>
        using namespace std;
         
        #define nl "\n"
        #define sp ' '
        void __print(int x) {cerr << x;}
        void __print(long x) {cerr << x;}
        void __print(long long x) {cerr << x;}
        void __print(unsigned x) {cerr << x;}
        void __print(unsigned long x) {cerr << x;}
        void __print(unsigned long long x) {cerr << x;}
        void __print(float x) {cerr << x;}
        void __print(double x) {cerr << x;}
        void __print(long double x) {cerr << x;}
        void __print(char x) {cerr << '\'' << x << '\'';}
        void __print(const char *x) {cerr << '\"' << x << '\"';}
        void __print(const string &x) {cerr << '\"' << x << '\"';}
        void __print(bool x) {cerr << (x ? "true" : "false");}
 
        template<typename T, typename V>
        void __print(const pair<T, V> &x) {cerr << '{'; __print(x.first); cerr << ','; __print(x.second); cerr << '}';}
 
        template<typename T>
        void __print(const T &x) {
            int f = 0;
            cerr << '{';
            for (auto &i : x) cerr << (f++ ? "," : ""), __print(i);
            cerr << '}';
        }
 
        void _print() {cerr << "]\n";}
        template <typename T, typename... V>
        void _print(T t, V... v) {
            __print(t);
            if (sizeof...(v)) cerr << ", ";
            _print(v...);
        }
 
        #ifndef ONLINE_JUDGE
        #define debug(x...) cerr << "[" << #x << "] = ["; _print(x)
        #else
        #define debug(x...)
        #endif
 
        using ll= long long;
        using db=double;
        using ldb=long double;
        #define vi vector<ll>
        #define vvi vector<vector<ll>>
        #define pii pair<ll,ll>
        #define vpii vector<pair<ll,ll>>
        #define ff first
        #define ss second
        #define mii map<ll,ll>
        #define umii unordered_map<ll,ll> 
        #define spii set<pair<ll,ll>>
        #define all(v)        (v).begin(), (v).end()
        #define forw(i,x,y) for(ll i=x;i<y;i++)
        #define sorting(v) sort(v.begin(),v.end())
        #define reversing(v) reverse(v.begin(),v.end())
        #define pb(v,a) v.push_back(a)
        #define fast ios_base::sync_with_stdio(false); cin.tie(NULL); cout.tie(NULL)
        #define IA(a, n) for (ll i = 0; i < n; i++) cin >> a[i];
        #define fo(i, n) for (ll i = 0; i < n; i++)
        #define lcm(m, n)            ((m / __gcd(m, n))*n)
        #define min_ele(v)           *min_element(all(v))
        #define max_ele(v)           *max_element(all(v))
        const ll mod=1000000007;
        const ll inf=LLONG_MAX;
        #define yes cout<<"YES" 
        #define no cout<<"NO" 
        // helper functions
        bool odd(ll num) { return ((num & 1) == 1); }
        bool even(ll num) { return ((num & 1) == 0); }
        ll nCk(ll n, ll k) {
            ll res = 1;
            for (ll i = 0; i < k; i++) {
                res = res * (n - i);
                res = res / (i + 1);
            }
            return res;
        }
         
        bool iBi(ll x, ll low, ll high) {
            return x >= low && x <= high;
        }
        bool iBe(int x, int low, int high) {
        return x > low && x < high;
    }
      
 
    ll powmod(ll a, ll b, ll m) {
        ll res = 1;
        a %= m;
        while (b > 0) {
            if (b & 1) res = (res * a) % m;
            a = (a * a) % m;
            b >>= 1;
        }
        return res;
    }
 
         ll modinv(ll b, ll m=mod) {
        return powmod(b, m - 2, m);
    }
         
        bool compare(pii a,pii b){
            if(a.ff!=b.ff) return a.ff>b.ff; //desc order of first value
            return a.ss<b.ss; //lower index for same value
         
        }
        bool isInteger(double num) {
            return floor(num) == num;
        }
         
        string getBinary(ll num) {
        if (num == 0) return "0";
 
        string binary = "";
        while (num > 0) {
            binary += (num % 2 == 0 ? '0' : '1');
            num /= 2;
        }
        reverse(binary.begin(), binary.end());
        return binary;
        }
        // long long ceil 
        long long ceil_div(long long a, long long b) {
        return (a + b - 1) / b;
    }
        ll binarySearch(const vector<ll>& arr, ll target) {
        ll low = 0, high = arr.size() - 1;
 
        while (low <= high) {
            ll mid = low + (high - low) / 2;  // To avoid overflow
 
            if (arr[mid] == target)
                return mid;  // Found at index mid
            else if (arr[mid] < target)
                low = mid + 1;
            else
                high = mid - 1;
        }
 
        return -1;  // Not found
    }
        ll binarySearchDesc(const vector<ll>& arr, ll target) {
        ll low = 0, high = arr.size() - 1;
 
        while (low <= high) {
            ll mid = low + (high - low) / 2;
 
            if (arr[mid] == target)
                return mid;
            else if (arr[mid] > target)  // Move right
                low = mid + 1;
            else                          // Move left
                high = mid - 1;
        }
        return -1;
    }
 
         //Matrix:  vector<vector<ll>> matrix(n, vector<ll>(m));
        //array import
        //ll n;
        // cin>>n;
        // vi a(n);
        // IA(a,n)
        //prefixsum
        // vi prefsum(n);
        // prefsum[0]=b[0];
        // forw(i,1,n){
        //     prefsum[i]=prefsum[i-1]+b[i];
        // }
        // input array a in fxn const vi& a
    // or declare global array in main take a.resize(n) then input in it
 
        // vi prefsum(n);
        // prefsum[0]=a[0];
        // forw(i,1,n){
        //     prefsum[i]=a[i]+prefsum[i-1];
        // }
 
        //upper bound
        // ll y=upper_bound(a.begin(),a.end(),r)-a.begin();
 
        //unique fxn
        //  auto it = unique(a.begin(), a.end());
        // a.erase(it, a.end());
    // to convert string 111000111 to arrray
        // for (char c : s1) {
        //         a.push_back(c - '0');
        //     }
 
        // uSE 1LL<<N NOT 1<<N;
        // ------------------------------------------SOLUTION------------------------------------------
 
 
    
 
         
    void solve() {
        ll n,k,x,a,b,c;
        cin>>n>>k>>x>>a>>b>>c;
        vi v;
        v.push_back(x);
        forw(i,1,n){
            ll op=(a*v[i-1]+b)%c;
            v.push_back(op);
        }
        
        deque<ll> dq;
        debug(v);
        vi res;
        fo(i,n){
            if(!dq.empty() && dq.front()<=i-k)
                dq.pop_front();

            while(!dq.empty() && v[dq.back()]>=v[i]) //sare bade element delete
                dq.pop_back();

            dq.push_back(i);

            if(i>=k-1) 
                {res.push_back(v[dq.front()]);
                    cout<<dq.front()<<sp;}
            debug(dq);
        }
        cout<<nl;
        ll ans=0;
        for(auto b:res){
            cout<<b<<sp;
        }

    }
 
 
 
 
     
 
 
        bool multi = false;
        int32_t main(){
            fast;
            int t = 1;
            if (multi)cin >> t;
 
 
            while(t--){
                solve();
                cout<<"\n";
            }
            return 0;
        }
