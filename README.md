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
<li>Given that it is an online bank, it is crucial <b>to separate the LAN from the WAN through a DMZ </b>to minimize unauthorized access to internal sensitive data while optimizing a secure user experience.</li>
<li>Implement <b>firewalls</b> between each zone and other <b>malware detection and prevention solutions</b> within the network: antivirus software, IPS/IDS...</li>
<li>Establish a <b>Two-Factor Authentication (2FA)</b> system for users accessing their banking accounts, as well as a separate one for employees.</li>
<li>Acknowledging that employees may work remotely from public or home networks, which are typically less secure and more vulnerable than the company's one, implementing stringent telework policies that include <b> the use of VPNs and device segmentation to separate personal and professional operations.</b> </li>
<li>Using <b>encryption techniques</b> to protect data both in transit and at rest.</li>
<li>Set up backup servers.</li>
<li>🥁 Not to forget <b> DDoS attacks </b> 
</br></br>
    <img src="https://media0.giphy.com/media/v1.Y2lkPTc5MGI3NjExOGVwMjloMGlidXdpemtuZmgyY2diOXJobW92eHo3dW9tbjY4dmQ2bSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/f0TvnEmF5yPLO/giphy.webp" width="150" height="150" alt="Gif">
</br></br> -> Implement a load balancer positioned after the DMZ router to distribute traffic.
</br> -> Establish a backup DNS server to mitigate DDoS attacks; in case of an attack on the website, users can be redirected to another server.
</li>
</ul>
</p>
