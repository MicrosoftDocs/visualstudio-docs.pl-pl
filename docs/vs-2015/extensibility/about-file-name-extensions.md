---
title: Temat rozszerzeń nazw plików | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- file extensions
- file name extensions
ms.assetid: 99f4f9ff-fb84-4258-9787-6890f308a57f
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 866a30279ca2c79f4a490a040f76bc3a86c6a6e1
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54759108"
---
# <a name="about-file-name-extensions"></a>Informacje o rozszerzeniach nazw plików
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Po zarejestrowaniu rozszerzenie pliku pakietu VSPackage, należy ją skojarzyć z wersją [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Jest to ważne, jeśli więcej niż jedna wersja [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] jest zainstalowany na komputerze.  
  
 Rozszerzenia plików dla pakietów VSPackage są rejestrowane w kluczu HKEY_CLASSES_ROOT z wartością domyślną, który wskazuje na skojarzony identyfikator programowy (ProgID).  
  
 Oto przykład informacji o rejestracji dla .vcproj rozszerzenie pliku:  
  
```  
HKEY_CLASSES_ROOT\  
   .vcproj\  
      (default)=" VisualStudio.vcproj.8.0"   
```  
  
 Plików skojarzonych z [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] musi mieć określonej wersji ProgID, takich jak `VisualStudio.vcproj.8.0`, aby umożliwić instalacje side-by-side produktu do utrzymania skojarzenia rozszerzeń plików między wersji produktu. ProgID specyficzny dla wersji pozwala również na używanie zleceń standardowych, takie jak edytowanie otwarte i tak dalej, bez obawy, zastępowanie lub zastąpieniem przez inne aplikacje lub wersje [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
 W niektórych przypadkach także identyfikator ProgID skojarzone z rozszerzeniem pliku nie powinna być zmieniana. Na przykład identyfikator ProgID rozszerzeniem pliku .htm (progid = htmlfile) jest zakodowana w wielu miejscach w systemie operacyjnym i jest powszechnie znane i używane w połączeniu z pliki htm i HTML.  
  
## <a name="see-also"></a>Zobacz też  
 [Rejestrowanie rozszerzeń nazw plików dla wdrożeń Side-By-Side](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)   
 [Określanie programów obsługi plików dla rozszerzeń nazw plików](../extensibility/specifying-file-handlers-for-file-name-extensions.md)
