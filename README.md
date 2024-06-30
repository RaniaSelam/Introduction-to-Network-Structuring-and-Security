<h1 align="center">Introduction-to-Network-Structuring-and-Security</h1>

<p>
For this project, we will be creating and structuring a complete organization's network. For this case, we will base ourselves on a fake online bank named "Bankurity", which we will have to secure in the most efficient and practical way we can.

In the context of the actual project, once the theoretical plan is ready, we are supposed to replicate it using virtual machines (VMs), simplifying it before if necessary.

Keep in mind that the goal is not to create a complex or advanced architecture, but rather something simple and clean to help beginners properly grasp the concepts.

Throughout this guide, we will be focusing on the theoretical aspect. Feel free to take it further with the VMs if you wish. If you do, don't hesitate to share your progress with me 😊
</p>
<h2>
Let's get started!
</h2>
</br>
<h3>Prerequisites</h3>
<p>
Before we begin, for those who have never approched networking before, I strongly recommend familiarizing yourself with the basics at least first. You can check out the <a href="https://www.w3schools.com/cybersecurity/cybersecurity_networking.php">W3School Cyber Security Networking Basics</a> section of their Cybersecurity Introduction Course, which is informative but concise enough.

Moving forward, you'll need a platform that suits you to create your network diagram. Personally, I use <a href="https://isoflow.io/">Isoflow</a>, which I find clear and user-friendly.
</p>
<h3>Start planning 📊</h3>
<p>
<b>The first step is always to understand the operational and cybersecurity needs of the given organization.</b>
</br>
I personnaly recommend listing your initial thoughts as a foundation before starting the structuring of your diagram, which you will of course probably implement later, and even significantly revise. However, this approach will help ensure you don't start with a lack of direction.
</br>
</br>
<b>🔎 Here are some challenges I tried identifying at my beginning of this project :</b>
<ul>
<li><img src="https://cdn-icons-png.flaticon.com/512/2758/2758737.png" width="15" alt="zones"> Given that it is an online bank, it is crucial <b>to separate the LAN from the WAN through a DMZ </b>to minimize unauthorized access to internal sensitive data while optimizing a secure user experience.</li>
<li><img src="https://cdn-icons-png.flaticon.com/512/811/811683.png" width="15" alt="firewall"> Implement <b>firewalls</b> between each zone and other <b>malware detection and prevention solutions</b> within the network: antivirus software, IPS/IDS...</li>
<li>🔐 Establish a <b>Two-Factor Authentication (2FA)</b> system for users accessing their banking accounts, as well as a separate one for employees.</li>
<li>💻 Acknowledging that employees may work remotely from public or home networks, which are typically less secure and more vulnerable than the company's one, implementing stringent telework policies that include <b> the use of VPNs</b> and <b>device segmentation to separate personal and professional operations.</b> </li>
<li><img src="https://cdn-icons-png.flaticon.com/512/2742/2742010.png" width="15" alt=encryption> Using <b>encryption techniques</b> to protect data both in transit and at rest.</li>
<li>🔁 Set up <b>backup servers.</b></li>
<li>🥁 Not to forget <b> preventing from DDoS attacks 🥁 </b> 
</br></br>
    <img src="https://media0.giphy.com/media/v1.Y2lkPTc5MGI3NjExOGVwMjloMGlidXdpemtuZmgyY2diOXJobW92eHo3dW9tbjY4dmQ2bSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/f0TvnEmF5yPLO/giphy.webp" width="150" height="150" alt="Gif">
</br></br>-> Implement a load balancer positioned after the DMZ router to distribute traffic.
</br>-> Establish a backup DNS server to mitigate DDoS attacks; in case of an attack on the website, users can be redirected to another server.
</li>
</ul>
</p>
<h3>Create your base architecture 🔨</h3>
<p>
Once you have a general idea of the needs and solutions you want to implement, the next step is to create a representation of your network using your diagram platform! 
</br>To help you visualize, here's what my initial architecture based on the identified needs looked like :
</br></br> <b>PS : I apologize for the legends being in French (cuz we keep it real here), but it should be mainly understandable. 
</br>Anywhow, they are listed after the diagram for more clarity :).</b>
</p>
<div align="center">
<img src="https://github.com/RaniaSelam/Introduction-to-Network-Structuring-and-Security/assets/173706533/af627238-aa6d-4c0d-885d-f46188976c7c" width="800" alt="diagram">
</div>
<h3>Equipements on the diagram : </h3>
<p>
<ul>
<li>
<b>WAN :</b> 
</br>- Client :Router - Smartphone - Laptop
</br>- Telework : Router - Desktop - PC - Laptop
</li>
</br><li>
<b>DMZ:</b> 
</br>DMZ router -> Load Balancer -> DMZ switch -> [Client Data Server - Mail Server - Interface and Site Server - Client File Management Server - Technical Servers (DNS, NTP, DHCP...)]<- Admin 1 </li>
</br><li>
<b>In between the WAN and the DMZ :</b> 
</br>internet Router - Antivirus - IPS - Clients' authentification - Firewall 1
</li></br>
<li><b>LAN:</b> NIPS - LAN router - LAN switch - Backup router - Banking router - Admin 2
</br>- Workstations :  Printers - Desktop PC 1 - Desktop PC 2
</br>- Bank Management : Transfer Server - Funds and Vault Server - Investment Server
</br>- Backup : Backup Servers
(Web Services Backup, Audit and Security Logs Backup, Regulatory Documents Backup, Transaction Data Backup, Enterprise Databases Backup, Client Databases Backup)
</li></br>
<li><b>In between the DMZ and the LAN :</b> 
</br>Employes' authentification - Firewall 2
</li>
</ul>
</p>
<h3>How does it work? 🧐</h3>
<p>
Incoming traffic from the outside through the internet can be of two types: <b>client</b> or <b>remote employee</b>.

For this, an initial <b>2FA authentication</b> takes place for client access, preceding a <b>first firewall</b> marking the entry to the DMZ.

This first firewall manages the entry of traffic into the <b>DMZ</b>, where services usable by both clients and worekers are found, with differentiated access, of course. A <b>load balancer</b> is positioned between the <b>DMZ router</b> and the <b>switch</b> to distribute traffic among the servers and potentially protect against DDOS attacks.

The services found here include the <b>web interface</b>  and the <b>mail one</b>, <b>client file management</b> and their <b>data server</b>, and finally, the <b>technical servers</b> listed earlier but represented on the infrastructure by a single technical server. There is also an <b>admin</b> for the management and maintenance of the DMZ.

We arrive at the <b>intranet</b>! which constitutes the most sensitive part of the network. At its entrance, there is a <b>second authentication</b> reserved for employees, positioned before the <b>second firewall</b> that manages incoming and outgoing flows between the intranet, DMZ services, and remote workers. It is followed by a <b>NIPS</b> that inspects incoming packets and can stop malicious traffic that would have passed through the firewall.

The enterprise router here segments the intranet into <b>four distinct VLANs</b> according to their functions. One VLAN for <b>bank management</b> (covering transfers, investment funds, and so on), a backup VLAN for the <b>backup servers</b> that are also listed in the equipements and represented by these backup servers, a VLAN for the <b>workstations</b>, and finally, a VLAN for the <b>intranet admin</b>.
</p>
<h3>IP adressing</h3>
<p>
Next step is to assign an IP addressing to its network. To do so, and since we're assuming working with a small business, to start with, I recommend choosing a Class C notation.
</br></br>💡 <b>A Class C IP network uses a subnet mask of 255.255.255.0, which allows for 256 available IP addresses. </b>💡
</br></br>However, among these addresses, one being reserved for the network address and another for the broadcast address, we're left with 254 IP addresses usable for devices on the network, which is not too much but just enough if the company plans to grow some more :)
</br></br>
You can then assign and organize your IP addressing on an <b>IP addressing table</b> as follows :
</p>
<img src="https://github.com/RaniaSelam/Introduction-to-Network-Structuring-and-Security/assets/173706533/1edecc10-fc78-445a-aea1-1fc5f3826381" width = "500" alt="ip_table">
<h3>Firewall configuration</h3>
<p>A firewall configuration defines how network traffic is allowed or blocked based on predefined rules.
</br>It generally is represented on a <b>flow matrice</b> defined by <b>the source</b> of the traffic, its <b>destination</b> and <b>type of communication</b> as follows :
</br></br><img src="https://github.com/RaniaSelam/Introduction-to-Network-Structuring-and-Security/assets/173706533/6722da0f-06ee-4326-9253-31ec76a7bc77" width="295"  alt="flow_matrice_p1">
<img src="https://github.com/RaniaSelam/Introduction-to-Network-Structuring-and-Security/assets/173706533/a658ad23-96d8-47a3-aca5-cb53d2979949" width="300" alt="flow_matrice_p1">
<img src="https://github.com/RaniaSelam/Introduction-to-Network-Structuring-and-Security/assets/173706533/b8bdf020-b2b2-4ced-94bd-6352748ffe12" width="328" margin-top="0" alt="flow_matrice_p1">
</p>
<h3>To go further 🚀</h3>
<p>
If you ever decide to apply your network to VMs, you will most likely need to simplify it and reduce unnecessary servers to ensure everything runs smoothly.
</br>Here's an idea for a simplified network diagram based on the network we've seen in this guide if it could ever help you :
</br><div align="center">
<img src="https://github.com/RaniaSelam/Introduction-to-Network-Structuring-and-Security/assets/173706533/cdc2b245-f871-4b58-94dd-309a170cc1d7" width="700" alt="simplified_diagram">
</div>
<br> Also, if you do go through with it, it would be interesting to conduct penetration tests on your network to assess its security.
<h2>Good luck !✨</h2>
</p>
