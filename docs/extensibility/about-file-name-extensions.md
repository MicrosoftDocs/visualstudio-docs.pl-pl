---
title: Informacje o rozszerzeniach nazw plików | Microsoft Docs
description: Dowiedz się, jak zarejestrować rozszerzenia nazw plików dla pakietów VSPackage i skojarzyć je z określoną wersją programu Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- file extensions
- file name extensions
ms.assetid: 99f4f9ff-fb84-4258-9787-6890f308a57f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f38bee1b62340f7d557ac2e5190fc5c48d9268fe
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105060149"
---
# <a name="about-file-name-extensions"></a>Informacje o rozszerzeniach nazw plików
Po zarejestrowaniu rozszerzenia pliku pakietu VSPackage należy skojarzyć go z wersją programu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Jest to ważne, jeśli [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] na komputerze jest zainstalowana więcej niż jedna wersja programu.

 Rozszerzenia plików dla pakietów VSPackage są rejestrowane w kluczu **HKEY_CLASSES_ROOT** z wartością domyślną wskazującą na skojarzony identyfikator programowy (PROGID).

 W poniższym przykładzie przedstawiono informacje o rejestracji dla rozszerzenia pliku *. vcproj* :

```
HKEY_CLASSES_ROOT\
   .vcproj\
      (default)=" VisualStudio.vcproj.8.0"
```

 Pliki skojarzone z programem [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] muszą mieć wersję ProgID, taką jak `VisualStudio.vcproj.8.0` . Wersja ProgID umożliwia równoczesną instalację produktu w celu utrzymania skojarzeń rozszerzeń plików między wersjami produktów. Identyfikator ProgID specyficzny dla wersji umożliwia również korzystanie z czasowników standardowych, takich jak otwieranie, edytowanie i tak dalej, bez względu na zastępowanie lub zastępowanie innych aplikacji lub wersji programu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

 W niektórych przypadkach nie należy zmieniać identyfikatora ProgID skojarzonego z rozszerzeniem pliku. Na przykład identyfikator ProgID dla rozszerzenia pliku *. htm* (ProgID = HTMLFILE) jest zakodowany w wielu miejscach w systemie operacyjnym i jest powszechnie znany i używany w połączeniu z plikami *. htm* i *. html* .

## <a name="see-also"></a>Zobacz też
- [Rejestrowanie rozszerzeń nazw plików dla wdrożeń równoległych](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)
- [Określ programy obsługi plików dla rozszerzeń nazw plików](../extensibility/specifying-file-handlers-for-file-name-extensions.md)
