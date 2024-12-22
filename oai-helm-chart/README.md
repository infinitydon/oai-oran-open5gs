helm plugin install https://github.com/ThalesGroup/helm-spray

helm dependency update

helm -n telco spray . --create-namespace

kubectl multinet -n telco

### Note: I had to use eth0 for the N4 interface on SMF and UPF because UPF will not be able to communicate with NRF if all the interfaces are using Multus and NRF is not
### Alternative might be to use multus for the SBIs and put the N4 interfaces in the same subnet as the SBI

ping -I uesimtun0 192.168.22.3 -c 4

ping -I uesimtun0 4.2.2.2 -c 4

curl --interface uesimtun0 192.168.22.3

for i in $(helm -n telco ls | grep -v NAME | awk '{print $1}');do helm -n telco delete $i;done