## Project 7 - WordPress Pentesting

Time spent: **8** hours spent in total

> Objective: Find, analyze, recreate, and document **five vulnerabilities** affecting an old version of WordPress

## Pentesting Report

1. (Required) Authenticated Stored Cross-Site Scripting (XSS)
  - [ ] Summary:
      A stored XSS vulnerability in WordPress allows the user with the posting capability to compromise the website. Under default 
      configuration, the attack requires a Contributor or Author level account. The attacker would insert specially formatted HTML 
      containing JavaScript on a WordPress page or post. Some special configurations may allow posting or editing page content for 
      unauthenticated users.
    - Vulnerability types: Cross-Site Scripting (XSS)
    - Tested in version: 4.2.2
    - Fixed in version: 4.2.3
    
  - [ ] GIF Walkthrough:
    <img src="https://github.com/vaidehirana/IST-590---Week-7-Project/blob/master/Vulnerability%202.gif" widtch="800">
  
  - [ ] Steps to recreate:
      Admin login then go to posts and creates a new post with the HTML code ``` “<a href="[caption code=">]</a><a title=" 
      onmouseover=alert('Carefull!!!')  ">link</a>” ``` The post is then updated and when clicked view page it will redirect to the page 
      with the post. When you see the post there is a link and when user or admin mouse over it will give the XSS message.
  
  - [ ] Affected source code:
     - [Link 1](https://wpvulndb.com/wordpresses)
      
2. (Required) Unauthenticated Stored Cross-Site Scripting (XSS)
  - [ ] Summary:
      If the comment text is long enough, it will be truncated when inserted in the database. The MySQL TEXT type size limit is 64             kilobytes, so the comment must be quite long. The truncation results in malformed HTML generated on the page. The attacker can 
      supply any attributes in the allowed HTML tags but instead of using an invalid character to truncate the comment, this time an 
      excessively long comment is used for the same effect.
  
    - Vulnerability types: Cross-Site Scripting (XSS)
    - Tested in version: 4.2
    - Fixed in version: 4.2.1
    
  - [ ] GIF Walkthrough: 
    <img src="https://github.com/vaidehirana/IST-590---Week-7-Project/blob/master/Vulnerability%203.gif" widtch="800">
  
  - [ ] Steps to recreate: 
      Admin login then create a post or use existing post and log out from the page and then an user add comment to the posts which is 
      64 kb or larger. The comment would be ``` “<a title='x onmouseover=alert(unescape(/hello%20world/.source)) 
      style=position:absolute;left:0;top:0;width:5000px;height:5000px  AAAAAAAAAAAA...[64 kb]..AAA'></a>” ``` and it should go upto 64 
      kb for this vulnerability to be seen. Once the comment is posted the XSS message pops up.
  
  - [ ] Affected source code:
    - [Link 1](https://wpvulndb.com/wordpresses)
    
3. (Required) ClickkJacking (CSRF)
  - [ ] Summary: The clickjacking works when an User or Admin posts a comment which has malicious website embedded in the HTML code and 
      the code shows the website that is vulnerable to clickjacking
      
    - Vulnerability types: CSRF
    - Tested in version: 4.2
    - Fixed in version: 4.2.2
    
  - [ ] GIF Walkthrough: 
      <img src="https://github.com/vaidehirana/IST-590---Week-7-Project/blob/master/Vulnerability%204.gif" width="800">
  
  - [ ] Steps to recreate: 
      User or Admin login to the WordPress under the posts add a comment with the following HTML code
     ```
     "<html>
       <head>
         <title>Clickjack test page</title>
       </head>
       <body>
         <p>Website is vulnerable to clickjacking!</p>
         <iframe src="http://www.target.site" width="500" height="500"></iframe>
       </body>
      </html>"
      ```
      Once the user clicks submit button the website would show clickkJacking vulnerability with a malicious website.

  - [ ] Affected source code:
    - [Link 1](https://wpvulndb.com/wordpresses)
    
4. (Optional) Fingerprinting 'http://wpdistillery.vm/readme.html' (wordpress file) exists exposing a version number
  - [ ] Summary: 
      I can see the version number which is not updated to the current 4.9. and so I can find the vulnerabilities that are in the old 
      version of wordpress and try attacking it
    - Vulnerability types:
    - Tested in version: 4.2
    - Fixed in version: not fixed yet
    
  - [ ] GIF Walkthrough:
    <img src="https://github.com/vaidehirana/IST-590---Week-7-Project/blob/master/Vulnerability%201.gif" width="800">

  - [ ] Steps to recreate: 
      When I opened the readme file I was able to see the current installed version of wordpress
        
  - [ ] Affected source code:
    <img src="https://github.com/vaidehirana/IST-590---Week-7-Project/blob/master/Vulnerability%201.1.JPG" width="800">
    

5. (Optional) Vulnerability Name or ID
  - [ ] Summary: 
    - Vulnerability types:
    - Tested in version:
    - Fixed in version: 
  - [ ] GIF Walkthrough: 
  - [ ] Steps to recreate: 
  - [ ] Affected source code:
    - [Link 1](https://core.trac.wordpress.org/browser/tags/version/src/source_file.php) 

## Assets

List any additional assets, such as scripts or files

## Resources

- [WordPress Source Browser](https://core.trac.wordpress.org/browser/)
- [WordPress Developer Reference](https://developer.wordpress.org/reference/)

GIFs created with [LiceCap](http://www.cockos.com/licecap/).

## Notes

Describe any challenges encountered while doing the work

## License

    Copyright [yyyy] [name of copyright owner]

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

        http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
