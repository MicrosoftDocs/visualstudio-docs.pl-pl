---
title: Udzielanie zaufania do rozwiązań pakietu Office
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- security [Office development in Visual Studio], trust
- inclusion lists [Office development in Visual Studio], about inclusion lists
- trust [Office development in Visual Studio], 2007 Office system
- granting trust [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 50eeba9769bcfb54a38cd458e85988d2a679b687
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2018
ms.locfileid: "53648729"
---
# <a name="grant-trust-to-office-solutions"></a>Udzielanie zaufania do rozwiązań pakietu Office
  Udzielanie zaufania Office solutions oznacza, że modyfikowanie zasad zabezpieczeń dla każdego komputera docelowego zaufania zestawu rozwiązania, manifest aplikacji, manifest wdrożenia i dokumentu. Do rozwiązania dla pakietu Office można udzielić zaufania przez Ciebie lub użytkownika końcowego.  
  
 Aby przyznać pełne zaufanie do rozwiązania dla pakietu Office, należy podpisywanie manifestów aplikacji i wdrożenia.  
  
 Użytkownicy końcowi mogą udzielenia zaufania rozwiązania dla pakietu Office przy podejmowaniu decyzji zaufania w [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] monit o udzielenie zaufania.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
##  <a name="Signing"></a> Zaufanie rozwiązaniu przez podpisanie manifestów aplikacji i wdrożenia  
 Wszystkich aplikacji i wdrażania manifestów Office solutions muszą być podpisane za pomocą certyfikatu, który identyfikuje wydawcy. Certyfikaty posłużyć jako podstawa podejmowania decyzji dotyczących zaufania.  
  
 Tymczasowy certyfikat jest tworzony i przyznane zaufania w czasie kompilacji, dzięki czemu rozwiązanie będzie uruchamiany podczas jej debugowania. W przypadku publikowania rozwiązania, które jest podpisany przy użyciu tymczasowy certyfikat użytkownikowi końcowemu zostanie monit do podjęcia decyzji o zaufaniu.  
  
 Jeśli utworzysz rozwiązania przy użyciu znanego i zaufanego certyfikatu, automatycznie można zainstalować rozwiązania bez monitowania użytkownika końcowego do podjęcia decyzji o zaufaniu. Aby uzyskać więcej informacji o sposobie uzyskiwania certyfikatu podpisywania, zobacz [ClickOnce i podpis Authenticode](/visualstudio/deployment/clickonce-and-authenticode). Po uzyskaniu certyfikatu certyfikat musi być jawnie uznawany za zaufany przez dodanie go do listy zaufanych wydawców. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie zaufanego wydawcy do komputera klienckiego dla aplikacji ClickOnce](/visualstudio/deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications).  
  
 Jeśli Deweloper rejestruje rozwiązania z certyfikatem tymczasowe, administrator może ponownie podpisać dostosowania przy użyciu znanego i zaufanego certyfikatu przy użyciu Manifest Generation i narzędzia do edycji (*mage.exe*), które jest jednym z Microsoft .NET Framework narzędzia. Aby uzyskać więcej informacji na temat podpisywania rozwiązania zobacz [jak: Podpisywanie rozwiązań pakietu Office](../vsto/how-to-sign-office-solutions.md) i [jak: Podpisywanie manifestów aplikacji i wdrożenia](/visualstudio/ide/how-to-sign-application-and-deployment-manifests).  
  
##  <a name="TrustPrompt"></a>Zaufania rozwiązania przy użyciu monit o udzielenie zaufania ClickOnce  
 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] monituje użytkownika końcowego podejmowanie decyzji zaufania, jeśli ma żadnych zasad całej organizacji, która ufa certyfikatu tego rozwiązania. Jeżeli użytkownik przyznaje zaufanie do rozwiązania, tworzony jest wpis listy dołączania, który zawiera adres URL i klucz publiczny do przechowywania tej decyzji dotyczącej zaufania. Podczas dostosowywania zaufanych jest uruchamiana później, użytkownik końcowy nie jest monitowany ponownie.  
  
 Administratorzy mogą wyłączyć [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] zaufany monit, lub zdecydować, czy wiersz ma być przeprowadzane tylko w przypadku rozwiązań, które są podpisane za pomocą certyfikatu Authenticode. Aby uzyskać więcej informacji na temat zmiany tych ustawień dla stref Mój komputer, LocalIntranet, Internet, TrustedSites: i UntrustedSites, zobacz [jak: Konfigurowanie funkcji ClickOnce zaufania monitowania](/visualstudio/deployment/how-to-configure-the-clickonce-trust-prompt-behavior).  
  
## <a name="see-also"></a>Zobacz także  
 [Zabezpieczanie rozwiązań pakietu Office](../vsto/securing-office-solutions.md)   
 [Udzielanie zaufania do dokumentów](../vsto/granting-trust-to-documents.md)   
 [Rozwiązywanie problemów z zabezpieczeniami rozwiązań pakietu Office](../vsto/troubleshooting-office-solution-security.md)   
 [Zagadnienia dotyczące zabezpieczeń określone dla rozwiązań pakietu Office](../vsto/specific-security-considerations-for-office-solutions.md)  
  
  