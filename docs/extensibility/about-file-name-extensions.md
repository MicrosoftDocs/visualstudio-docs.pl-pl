---
title: Temat rozszerzeń nazw plików | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- file extensions
- file name extensions
ms.assetid: 99f4f9ff-fb84-4258-9787-6890f308a57f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1146c7ed7bfc0d3f09d6c1848bf52345661bf0c7
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54995037"
---
# <a name="about-file-name-extensions"></a>Temat rozszerzeń nazw plików
Po zarejestrowaniu rozszerzenie pliku pakietu VSPackage, należy ją skojarzyć z wersją [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Jest to ważne, jeśli więcej niż jedna wersja [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] jest zainstalowany na komputerze.  
  
 Rozszerzenia plików dla pakietów VSPackage są zarejestrowane w obszarze **HKEY_CLASSES_ROOT** klucza z wartością domyślną, który wskazuje na skojarzony identyfikator programowy (ProgID).  
  
 W poniższym przykładzie przedstawiono informacje o rejestracji dla *.vcproj* rozszerzenie pliku:  
  
```  
HKEY_CLASSES_ROOT\  
   .vcproj\  
      (default)=" VisualStudio.vcproj.8.0"   
```  
  
 Plików skojarzonych z [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] musi mieć określonej wersji ProgID, takich jak `VisualStudio.vcproj.8.0`. Numerów wersji ProgID umożliwia instalacje side-by-side produktu do utrzymania skojarzenia rozszerzeń plików między wersji produktu. ProgID specyficzny dla wersji pozwala również na używanie zleceń standardowych, takie jak edytowanie otwarte i tak dalej, bez obawy, zastępowanie lub zastąpieniem przez inne aplikacje lub wersje [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 W niektórych przypadkach także identyfikator ProgID skojarzone z rozszerzeniem pliku nie powinna być zmieniana. Na przykład identyfikatora programu *.htm* rozszerzenie pliku (progid = htmlfile) jest ustalony w wielu miejscach w systemie operacyjnym, a jest powszechnie znane i używane w połączeniu z *.htm* i *.html* plików.  
  
## <a name="see-also"></a>Zobacz także  
 [Rejestrowanie rozszerzeń nazw plików dla wdrożeń side-by-side](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)   
 [Określanie programów obsługi plików dla rozszerzeń nazw plików](../extensibility/specifying-file-handlers-for-file-name-extensions.md)