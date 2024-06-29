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
<b>Here are some challenges I myself identified at my beginning of this project :</b>
<ul>
<li>Given that it is an online bank, it is crucial to separate the LAN from the WAN through a DMZ to minimize unauthorized access to internal sensitive data while optimizing a secure user experience.</li>
<li>Acknowledging that employees may work remotely from public or home networks, which are typically less secure and more vulnerable than the company's network: implementing stringent telework policies that include the use of VPNs and device segmentation to separate personal and professional operations.

</li>

  <li>Protect banking transaction flows on the network.</li>
</ul>
</p>
