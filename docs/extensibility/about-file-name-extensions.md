---
title: Rozszerzenia nazw plików – informacje | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- file extensions
- file name extensions
ms.assetid: 99f4f9ff-fb84-4258-9787-6890f308a57f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 03e07ec233ef975441a1f10507f0db872051558f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740347"
---
# <a name="about-file-name-extensions"></a>Rozszerzenia nazw plików – informacje
Podczas rejestrowania rozszerzenia pliku VSPackage, należy skojarzyć [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]go z wersją programu . Jest to ważne, jeśli [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] na komputerze jest zainstalowanych więcej niż jedną wersję.

 Rozszerzenia plików dla vspackages są rejestrowane **w** HKEY_CLASSES_ROOT klucz z wartością domyślną, która wskazuje na skojarzony identyfikator programowy (ProgID).

 W poniższym przykładzie przedstawiono informacje o rejestracji rozszerzenia pliku *.vcproj:*

```
HKEY_CLASSES_ROOT\
   .vcproj\
      (default)=" VisualStudio.vcproj.8.0"
```

 Pliki skojarzone [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] z musi mieć wersjonowane `VisualStudio.vcproj.8.0`ProgID, takich jak . Wersja ProgID umożliwia instalacje obok siebie produktu w celu utrzymania skojarzeń rozszerzenia plików między wersjami produktu. ProgID specyficzny dla wersji umożliwia również używanie standardowych czasowników, takich jak otwieranie, edytowanie i tak dalej, bez [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]obawy o nadpisywanie lub zastępowanie przez inne aplikacje lub wersje programu .

 W niektórych przypadkach nie należy zmieniać identyfikatora progid skojarzonego z rozszerzeniem pliku. Na przykład progid dla rozszerzenia pliku *.htm* (progid = htmlfile) jest zakodowany na miejscu w wielu miejscach w systemie operacyjnym i jest powszechnie znany i używany w połączeniu z *plikami .htm* i *.html.*

## <a name="see-also"></a>Zobacz też
- [Rejestrowanie rozszerzeń nazw plików dla wdrożeń side-by-side](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)
- [Określanie programów obsługi plików dla rozszerzeń nazw plików](../extensibility/specifying-file-handlers-for-file-name-extensions.md)
