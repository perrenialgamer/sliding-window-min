void solve() {
ll n,k;
       cin>>n>>k;
       vi v(n)
       IA(v,n)
       
        
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
