---
title: 'Instrukcje: Tworzenie manifestu pakietu | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- package files [Windows Installer]
- package files [ClickOnce]
- prerequisites, custom bootstrapper package
- dependencies, custom bootstrapper packages
ms.assetid: 5aecc507-2764-42f2-ae6f-c227971cf0af
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c711c50ab484cc88b1d6aff5c8e3018cead69953
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60046018"
---
# <a name="how-to-create-a-package-manifest"></a>Instrukcje: Tworzenie manifestu pakietu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby wdrożyć wymagania wstępne dotyczące aplikacji, można użyć pakietu programu inicjującego. Pakiet programu inicjującego zawiera pojedynczy plik manifestu produktu ale manifest pakietu dla poszczególnych ustawień regionalnych. Zestawu funkcji wspólnych w różnych wersjach zlokalizowanych powinny należeć do manifestu produktu.  
  
 Aby uzyskać więcej informacji na temat manifestów pakietu zobacz [jak: Tworzenie manifestu produktu](../deployment/how-to-create-a-product-manifest.md).  
  
## <a name="creating-the-package-manifest"></a>Tworzenie manifestu pakietu  
  
#### <a name="to-create-the-package-manifest"></a>Aby utworzyć manifest pakietu  
  
1. Utwórz katalog dla pakietu programu inicjującego. W tym przykładzie użyto C:\package.  
  
2. Utwórz podkatalog o nazwie ustawień regionalnych, np. en, w języku angielskim.  
  
3. W programie Visual Studio, należy utworzyć plik XML, który nosi nazwę `package.xml`i zapisz go w folderze C:\package\en.  
  
4. Dodaj kod XML, aby wyświetlić listę Nazwa pakietu programu inicjującego, kultura tego manifestu pakietu zlokalizowane i umowę licencyjną opcjonalne. Następujący kod XML używa zmiennych `DisplayName` i `Culture`, które są określone w elemencie nowsze.  
  
    ```  
    <Package  
        xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
        Name="DisplayName"  
        Culture="Culture"  
        LicenseAgreement="eula.txt">  
    ```  
  
5. Dodaj kod XML, aby wyświetlić listę wszystkich plików, które znajdują się w katalogu specyficzny dla ustawień regionalnych. Następujący kod XML, używany jest plik o nazwie eula.txt, który ma zastosowanie do **en** ustawień regionalnych.  
  
    ```  
    <PackageFiles>  
      <PackageFile Name="eula.txt"/>  
    </PackageFiles>  
    ```  
  
6. Dodaj kod XML do definiowania możliwych do zlokalizowania ciągi dla pakietu programu inicjującego. Następujący kod XML dodaje ciągi błędów dla ustawień regionalnych en.  
  
    ```  
      <Strings>  
        <String Name="DisplayName">Custom Bootstrapper Package</String>  
        <String Name="CultureName">en</String>  
        <String Name="NotAnAdmin">You must be an administrator to install   
    this package.</String>  
        <String Name="GeneralFailure">A general error has occurred while   
    installing this package.</String>  
    </Strings>  
    ```  
  
7. Skopiuj C:\package folder katalogu program inicjujący Instalatora programu Visual Studio. Dla programu Visual Studio 2010 to jest katalog SDKs\Windows\v7.0A\Bootstrapper\Packages \Program Files\Microsoft.  
  
## <a name="example"></a>Przykład  
 Manifest pakietu zawiera informacje specyficzne dla ustawień regionalnych, takie jak komunikaty o błędach, postanowienia licencyjne dotyczące oprogramowania i pakietów językowych.  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<Package  
  xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
  Name="DisplayName"  
  Culture="Culture"  
  LicenseAgreement="eula.txt">  
  
  <PackageFiles>  
    <PackageFile Name="eula.txt"/>  
  </PackageFiles>  
  
  <Strings>  
    <String Name="DisplayName">Custom Bootstrapper Package</String>  
    <String Name="Culture">en</String>  
    <String Name="NotAnAdmin">You must be an administrator to install this package.</String>  
    <String Name="GeneralFailure">A general error has occurred while   
installing this package.</String>  
  </Strings>  
</Package>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Produkt i pakiet — dokumentacja schematu](../deployment/product-and-package-schema-reference.md)
