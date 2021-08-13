# Install Pattern DNS Server

you can install this pattern with `YaST Software Management`

# Configuration

* Open YaST DNS Server

    ![](/assets/IMG/Screenshot_20210814_030839.png)

    just hit `Continue`

* Go to forwarder and input your ip address then click `Add`

    ![](/assets/IMG/Screenshot_20210814_031204.png)

* if you find like this just hit `OK`

    ![](/assets/IMG/Screenshot_20210814_031411.png)

* Go to `DNS Zones` and input your server name as your wish like `malik.local` then click `Add`

    ![](/assets/IMG/Screenshot_20210814_031808.png)

* Click `Edit` and you find screen like this

    ![](/assets/IMG/Screenshot_20210814_032124.png)

* Go to `NS Records` and input `ns.` before your server name then click `Add`

    ![](/assets/IMG/Screenshot_20210814_032313.png)

* Go to `MX Records` and do it yourself like this example

    ![](/assets/IMG/Screenshot_20210814_032421.png)

* Go to `Records` and just follow this example

    ![](/assets/IMG/Screenshot_20210814_032651.png)

* After finish all steps, just hit `ok`

# Testing

open browser

```
www.malik.local
```
```
mail.malik.local
```
```
ns.malik.local
```