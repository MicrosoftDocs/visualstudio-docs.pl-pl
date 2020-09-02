---
title: 'Instrukcje: tworzenie skojarzeń plików dla aplikacji ClickOnce | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697698"
---
# <a name="how-to-create-file-associations-for-a-clickonce-application"></a>Porady: tworzenie skojarzeń plików dla aplikacji ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacje mogą być skojarzone z jednym lub więcej rozszerzeniami nazw plików, dzięki czemu aplikacja zostanie uruchomiona automatycznie, gdy użytkownik otworzy plik tych typów. Dodawanie obsługi rozszerzenia nazwy pliku do [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacji jest proste.  
  
### <a name="to-create-file-associations-for-a-clickonce-application"></a>Aby utworzyć skojarzenia plików dla aplikacji ClickOnce  
  
1. Utwórz [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikację normalnie lub Użyj istniejącej [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacji.  
  
2. Otwórz manifest aplikacji za pomocą edytora tekstu lub XML, takiego jak Notatnik.  
  
3. Znajdź `assembly` element. Aby uzyskać więcej informacji, zobacz [manifest aplikacji ClickOnce](../deployment/clickonce-application-manifest.md).  
  
4. Jako element podrzędny `assembly` elementu Dodaj `fileAssociation` element. `fileAssociation`Element ma cztery atrybuty:  
  
   - `extension`: Rozszerzenie nazwy pliku, które chcesz skojarzyć z aplikacją.  
  
   - `description`: Opis typu pliku, który będzie wyświetlany w powłoce systemu Windows.  
  
   - `progid`: Ciąg unikatowo identyfikujący typ pliku, aby oznaczyć go w rejestrze.  
  
   - `defaultIcon`: Ikona do użycia dla tego typu pliku. Ikona musi być dodana jako zasób pliku w manifeście aplikacji. Aby uzyskać więcej informacji, zobacz [jak to zrobić: Dołączanie pliku danych do aplikacji ClickOnce](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md).  
  
     Aby zapoznać się z przykładem `file` `fileAssociation` elementów i, zobacz [ \<fileAssociation> element](../deployment/fileassociation-element-clickonce-application.md).  
  
5. Jeśli chcesz skojarzyć więcej niż jeden typ pliku z aplikacją, Dodaj dodatkowe `fileAssociation` elementy. Należy zauważyć, że `progid` atrybut powinien być różny dla każdego.  
  
6. Po zakończeniu pracy z manifestem aplikacji ponownie podpisz manifest. Można to zrobić z poziomu wiersza polecenia, używając Mage.exe.  
  
    `mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx`  
  
    Aby uzyskać więcej informacji, zobacz [Mage.exe (narzędzie tworzenia i edycji manifestów)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)  
  
## <a name="see-also"></a>Zobacz też  
 [\<fileAssociation> Postaci](../deployment/fileassociation-element-clickonce-application.md)   
 [Manifest aplikacji ClickOnce](../deployment/clickonce-application-manifest.md)   
 [Mage.exe (Narzędzie tworzenia i edycji manifestów)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)
