---
title: 'Instrukcje: Tworzenie skojarzeń plików dla aplikacji ClickOnce | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- file associations, ClickOnce applications
- ClickOnce deployment, file associations
ms.assetid: 835230c8-3177-440f-85e3-e40f1d8b4f9d
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 82ffecdc719dad2f38208de00dc95438b3ff36ef
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65697698"
---
# <a name="how-to-create-file-associations-for-a-clickonce-application"></a>Instrukcje: Tworzenie skojarzeń plików dla aplikacji ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacje mogą być skojarzone z jednego lub więcej rozszerzeń nazw plików, więc, że aplikacja będzie uruchamiana automatycznie kiedy użytkownik otwiera plik z tych typów. Dodaniem obsługi rozszerzenia nazwy pliku [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacji jest bardzo proste.  
  
### <a name="to-create-file-associations-for-a-clickonce-application"></a>Aby utworzyć skojarzenia plików dla aplikacji ClickOnce  
  
1. Tworzenie [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacji zwykle, lub użyj istniejącej [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacji.  
  
2. Otwórz manifest aplikacji przy użyciu tekstu lub edytorze XML, takiego jak Notatnik.  
  
3. Znajdź `assembly` elementu. Aby uzyskać więcej informacji, zobacz [Manifest aplikacji ClickOnce](../deployment/clickonce-application-manifest.md).  
  
4. Jako element podrzędny elementu `assembly` elementu Dodawanie `fileAssociation` elementu. `fileAssociation` Element ma cztery atrybuty:  
  
   - `extension`: Rozszerzenie nazwy pliku, który chcesz skojarzyć z aplikacją.  
  
   - `description`: Opis typu pliku, co pojawi się w usłudze Windows shell.  
  
   - `progid`: Ciąg unikatowo identyfikujący typ pliku, aby oznaczyć go w rejestrze.  
  
   - `defaultIcon`: Ikona do użycia dla tego typu pliku. Ikony, należy dodać jako zasób w pliku w manifeście aplikacji. Aby uzyskać więcej informacji, zobacz [jak: Uwzględnianie pliku danych w aplikacji ClickOnce](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md).  
  
     Na przykład `file` i `fileAssociation` elementów, zobacz [ \<fileassociation — > Element](../deployment/fileassociation-element-clickonce-application.md).  
  
5. Jeśli chcesz skojarzyć więcej niż jeden typ pliku z aplikacją, Dodaj dodatkowe `fileAssociation` elementów. Należy pamiętać, że `progid` atrybut powinien być inne dla każdego.  
  
6. Po zakończeniu manifest aplikacji, należy ponownie podpisać manifest. Można to zrobić z wiersza polecenia przy użyciu Mage.exe.  
  
    `mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx`  
  
    Aby uzyskać więcej informacji, zobacz [Mage.exe (Manifest Generation i narzędzia do edytowania)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)  
  
## <a name="see-also"></a>Zobacz też  
 [\<fileAssociation> Element](../deployment/fileassociation-element-clickonce-application.md)   
 [Manifest aplikacji ClickOnce](../deployment/clickonce-application-manifest.md)   
 [Mage.exe (narzędzie generowania manifestu i edytowania)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)
