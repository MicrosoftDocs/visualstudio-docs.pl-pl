---
title: Informacje o rozszerzeniach nazw plików | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148038"
---
# <a name="about-file-name-extensions"></a>Informacje o rozszerzeniach nazw plików
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Po zarejestrowaniu rozszerzenia pliku pakietu VSPackage należy skojarzyć go z wersją programu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Jest to ważne, jeśli [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] na komputerze jest zainstalowana więcej niż jedna wersja programu.  
  
 Rozszerzenia plików dla pakietów VSPackage są rejestrowane w kluczu HKEY_CLASSES_ROOT z wartością domyślną wskazującą na skojarzony identyfikator programowy (ProgID).  
  
 Poniżej znajduje się przykład informacji rejestracyjnych dla rozszerzenia pliku. vcproj:  
  
```  
HKEY_CLASSES_ROOT\  
   .vcproj\  
      (default)=" VisualStudio.vcproj.8.0"   
```  
  
 Pliki skojarzone z programem [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] muszą mieć posiadaną wersję ProgID, taką jak `VisualStudio.vcproj.8.0` , aby zezwolić na bezpośrednie instalacje produktu do obsługi skojarzeń rozszerzeń plików między wersjami produktów. Identyfikator ProgID specyficzny dla wersji umożliwia również korzystanie z czasowników standardowych, takich jak otwieranie, edytowanie i tak dalej, bez względu na zastępowanie lub zastępowanie innych aplikacji lub wersji programu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
 W niektórych przypadkach nie należy zmieniać identyfikatora ProgID skojarzonego z rozszerzeniem pliku. Na przykład identyfikator ProgID dla rozszerzenia pliku. htm (ProgID = HTMLFILE) jest zakodowany w wielu miejscach w systemie operacyjnym i jest powszechnie znany i używany w połączeniu z plikami. htm i. html.  
  
## <a name="see-also"></a>Zobacz też  
 [Rejestrowanie rozszerzeń nazw plików dla wdrożeń równoległych](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)   
 [Określanie programów obsługi plików dla rozszerzeń nazw plików](../extensibility/specifying-file-handlers-for-file-name-extensions.md)
