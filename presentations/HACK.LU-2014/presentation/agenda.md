% Bettercrypto - Applied Crypto Hardening for Sysadmins
% L. Aaron Kaplan <kaplan@cert.at> ;  David Durvaux <david.durvaux@gmail.com>; Aaron Zauner <azet@azet.org>
% 2014/10/21
---------------------------



# Part 1:  Intro to the project

## Welcome 

![Neboltai](img/neboltai.png)

%{\centering
%  \includegraphics[width=.7\textwidth]{img/neboltai.png}\par
%  \vbox{\emph{Do not talk unencrypted}}
%}

---
# Overview 

  1. Intro & Motivation
  2. How we got started, how we work, what's there, what's missing, 
     how to use the guide
  3. History of Crypto in a nutshell
  4. Theory
  4. 10:10 __break__
  5. Theory (cont.)
  6. Attacks
  7. Current trends (IETF, ...)
  7. wrap up
  9. 11:45 __lunch__
    

# Prerequisites

  * Participants should have a basic knowledge of System administration and be
familiar with configuring Apache, nginx, etc.
  * Basic knowledge of crypto will help.

# Motivation

![NSA](img/nsa.png)

# Motivation (2)

Please note:

  * the leaks also revealed to non-democratic countries precise recipies on how to do country wide or even Internet-wide surveillance, traffic inspection and -modification, etc.
  * If politicians in other countries did not know how to do this, now they know!
  * If criminals did not know how to do this, now they know!

# The reaction

\centering { \textbf{Don't give them anything for free}\par
  It's your home, you fight! }


# The reaction (2)

  * We as humans are used to certain **modes** in communications:
spoken words tend to:
    * be forgotten over time ("data expires")
    * get modified/changed whenever "copied" (repeated)
    * get changed/modified over time  ("forgetfullness")
    * we tend to be not so harsh about them ("forgive")
    * have a limited geographic range ("town talk")
    * be very decentralized ("accoustic range")
  * digital traces/data tends to be:
    * stored for ever. Never modified by default
    * used against you in the future
    * very centralized
    * copied very easily
    * always searchable in O(log(n)) 
    
  
# The reaction (3)

\centering { \textbf{Crypto is the only thing that might still help}
\par
a.k.a.:\par
	``\textit{The Bottom Line Is That Encryption Does Work}'', Edward Snowden
}

# But where?

  * Ca. August 2013: Adi Kriegisch asks Aaron where he could find good recommendations on SSL settings.
  * Does that exist? At that time:
    - no ssllabs cookbook
    - only theoretical recommendations (ENISA, eCrypt II, NIST)
    - ioerror's duraconf settings are outdated
    - no practical copy & paste-able settings exist?


# Project plan

![Project plan](img/metalab-world-domination.jpg)


# Project plan  (srsly)

  * Do at least something against the **Cryptocalypse**
  * Check SSL, SSH, PGP crypto SeIngs in the most common services and certificates:
    –  Apache, Nginx, lighthNp
	–  IMAP/POP servers (dovecot, cyrus, ...) –  openssl.conf
	–  Etc.
  * Write down our experinces as guide
  * Create easy, copy & paste-able settings which are "OK" (as far as we know) for sysadmins.
  * Keep the guide short. There are many good recommendations out there written by cryptographers for cryptographers
  * Many eyes must check this!
  * Make it open source

  


# Why is this relevant for you?

  * You run networks and services. These are targets. If you believe it or not.
  * You produce code. Make sure it uses good crypto coding practices

  * However good crypto is hard to achieve
  * Crypto does not solve all problems, but it helps


# Who?

Wolfgang Breyha (uni VIE), David Durvaux (CERT.be), Tobias Dussa (KIT-CERT), L. Aaron Kaplan (CERT.at), Christian Mock (coretec), Daniel Kovacic (A-Trust), Manuel Koschuch (FH Campus Wien), Adi Kriegisch (VRVis), Ramin Sabet (A-Trust), Aaron Zauner (azet.org), Pepi Zawodsky (maclemon.at), IAIK, A-Sit, ...  


# Contents so far

  * Intro
  * Disclaimer 
  * Methods 
  * Theory
    * Elliptic Curve Cryptography 
    * Keylengths 
    * Random Number Generators 
    * Cipher suites – general overview & how to choose one
  * Recommendations on practical settings 
  * Tools 
  * Links 
  * Appendix


# Methods and Principles

C.O.S.H.E.R principle:
  * **C**ompletely
  * **O**pen 
  * **S**ource
  * **H**eaders
  * **E**ngineering and
  * **R**esearch

Methods:
  * Public review
  * commits get **discussed**
  * recommendations **need** references (like wikipedia)
  * Every commit gets logged
  * We need your review!


# How to commit

  * https://git.bettercrypto.org (master, read-only)
  * https://github.com/BetterCrypto/ (please clone this one & send PRs)

How?
  1. discuss the changes first on the mailinglist
  2. clone 
  3. follow the templates 
  3. send pull requests
  3. **split the commit into many smaller commits **
  4. don't be cross if something does not get accepted. 
  5. be ready for discussion
 
# Theory part

\[
i \hbar \frac{\partial}{\partial t}\Psi = \hat H \Psi
\]


# Some thoughts on ECC

  * Currently this is under heavy debate
  * Trust the Math
    * eg. NIST P-256 (http://safecurves.cr.yp.to/rigid.html)
    * Coefficients generated by hashing the unexplained seed c49d3608 86e70493 6a6678e1 139d26b7 819f7e90.
  * Might have to change settings tomorrow
  * Most Applications only work with NIST-Curves
  * Bottom line: we leave the choice of ECC yes or no to the reader. You might have to adapt again.
  * However, many server operators tend towards ECC  (speed)

# Keylengths

  * http://www.keylength.com/ 
  * Recommended Keylengths, Hashing algorithms, etc.
  * Currently:
    * RSA: >= 3248 bits (Ecrypt II)	
    * ECC: >= 256	
    * SHA 2+ (SHA 256,…)
    * AES 128 is good enough

# AES 128? Is that enough?

\centering{,,On the choice between AES256 and AES128: I would never consider using AES256, just like I don’t wear a helmet when I sit inside my car. It’s too much bother for the epsilon improvement in security.''\par
— Vincent Rijmen in a personal mail exchange Dec 2013
}
  * Some theoretical attacks on AES-256






