---
title: Wybieranie między udostępnianymi i pakietów VSPackage z wersjami | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- SxS
- side-by-side installation
- installation [Visual Studio SDK], side-by-side
ms.assetid: e3128ac3-2e92-48e9-87ab-3b6c9d80e8c9
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 289e506d3cd404bba9a3a63d97179b89a948d381
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "67821982"
---
# <a name="choosing-between-shared-and-versioned-vspackages"></a>Wybieranie między udostępnionymi i wersjonowanymi pakietami VSPackage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Różne wersje programu Visual Studio mogą współistnieć na tym samym komputerze. Pakietów VSPackage może obsługiwać dowolne różne [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] wersje.  
  
 Instalacje równoległe programu pakietów VSPackage można włączyć za pomocą jednej z dwóch strategii, wspólnej strategii lub strategii wersji. Oba te funkcje są związane z obecnością wielu wersji [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] i skojarzonych wersji programu [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] .  
  
 W strategii udostępnionej jedna pakietu VSPackage jest zarejestrowana do użycia w wielu wersjach programu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . W strategii z wersjami są instalowane wiele bibliotek DLL pakietu VSPackage, po jednej dla każdej [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] obsługiwanej wersji.  
  
## <a name="shared-vspackages"></a>Udostępnione pakietów VSPackage  
 Użycie współużytkowanej pakietu VSPackage jest odpowiednie w przypadku używania tego samego pakietu VSPackage w wielu wersjach programu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Aby zaimplementować współużytkowany pakietu VSPackage, należy wykonać następujące czynności:  
  
- Pakietu VSPackage zgodność z wieloma wersjami programu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Dostępne są dwa sposoby wykonywania takich czynności:  
  
  - Ogranicz pakietu VSPackage do korzystania tylko z funkcji najstarszej [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] obsługiwanej wersji.  

  - Program pakietu VSPackage może dostosowywać do wersji, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] w której jest uruchomiona. Następnie, jeśli zapytania dotyczące nowszych usług zakończą się niepowodzeniem, pakietu VSPackage może oferować inne usługi, które są obsługiwane we wcześniejszych wersjach programu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
- Odpowiednio Zarejestruj pakietu VSPackage. Aby uzyskać więcej informacji, zobacz Rejestrowanie [pakietu VSPackage](../extensibility/internals/vspackage-registration.md) i [zarządzana Rejestracja pakietu VSPackage](https://msdn.microsoft.com/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1).  
  
- Odpowiednio Zarejestruj rozszerzenia plików. Aby uzyskać więcej informacji, zobacz [Rejestrowanie rozszerzeń nazw plików dla wdrożeń równoległych](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md).  
  
- Utwórz Instalatora, który wdraża pakietu VSPackage dla odpowiednich wersji programu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Aby uzyskać więcej informacji, zobacz [Installing pakietów VSPackage With Instalator Windows](../extensibility/internals/installing-vspackages-with-windows-installer.md) and [Management Components](../extensibility/internals/component-management.md).  
  
- Rozwiązywanie problemów z kolizjami rejestracji. Aby uzyskać więcej informacji, zobacz [pakietu VSPackage Registration](../extensibility/internals/vspackage-registration.md).  
  
- Upewnij się, że pliki udostępnione i w wersji uwzględniają zliczanie odwołań, aby umożliwić bezpieczną instalację i usuwanie wielu wersji. Aby uzyskać więcej informacji, zobacz [Zarządzanie składnikami](../extensibility/internals/component-management.md).  
  
## <a name="versioned-vspackages"></a>Pakietów VSPackage z wersjami  
 W ramach strategii pakietu VSPackage z wersjami można utworzyć jedną pakietu VSPackage dla każdej [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] obsługiwanej wersji. Jest to odpowiednie rozwiązanie, jeśli zamierzasz korzystać z usług oferowanych przez nowsze wersje programu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , ponieważ każdy pakietu VSPackage może się rozwijać bez wpływu na innych użytkowników. Niemniej jednak strategia z wersjami tworzenia wielu plików binarnych, z pojedynczej bazy kodu lub z wielu niezależnych baz kodu, może pociągać za sobą bardziej początkowe programowanie niż udostępniona strategia. Ponadto może być wymagana dodatkowa konfiguracja, ponieważ należy utworzyć osobną konfigurację dla każdej wersji lub pojedynczą konfigurację, która wykrywa wersje programu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , które są zainstalowane i które obsługuje pakietu VSPackage.  
  
## <a name="binary-compatibility"></a>Zgodność binarna  
 Ogólnie mówiąc, zgodność binarna umożliwia pakietów VSPackage kodu natywnego opracowanego we wcześniejszych wersjach programu Visual Studio do uruchomienia w nowszych wersjach programu Visual Studio. Istnieją jednak trzy ważne wyjątki:  
  
- Jeśli pakietu VSPackage zależy od określonej wersji środowiska uruchomieniowego języka wspólnego, należy określić, w jakiej wersji [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] jest uruchomiona.  
  
- Pakietu VSPackage może mieć zależność od określonej funkcji innego pakietu VSPackage lub innego produktu. W związku z tym pakietu VSPackage może działać tylko wtedy, gdy zależność jest spełniona.  
  
- Na pakietu VSPackage może mieć wpływ Poprawka zabezpieczeń w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] dodatku Service Pack lub w nowszej wersji programu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . W takich przypadkach pakietu VSPackage opracowana przy użyciu wcześniejszej wersji programu [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] może nie działać w wersjach programu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] po zastosowaniu poprawki zabezpieczeń. Można jednak ponownie skompilować pakiet przy użyciu nowszej wersji i uruchomić go również we wcześniejszych wersjach.  
  
  Zarządzane pakietów VSPackage muszą być kompilowane przy użyciu wersji programu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] i [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] zgodnej z wersją docelową [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
  Oprócz planowania zgodności binarnej plików binarnych pakietu VSPackage należy również rozważyć formaty plików rozwiązania i projektu. Jeśli pakietu VSPackage tworzy nowy typ projektu, należy zdecydować, czy może być uruchamiany tylko w jednej wersji, czy w wielu wersjach programu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Aby uzyskać więcej informacji, zobacz [uaktualnianie projektów niestandardowych](../misc/upgrading-custom-projects.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Instalowanie pakietów VSPackage z Instalator Windows](../extensibility/internals/installing-vspackages-with-windows-installer.md)   
 [Zarządzanie składnikami](../extensibility/internals/component-management.md)
