---
title: Temat rozszerzeń nazw plików | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- file extensions
- file name extensions
ms.assetid: 99f4f9ff-fb84-4258-9787-6890f308a57f
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 680f9e9f79430ea53da3566686b058c44894e494
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51776086"
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

