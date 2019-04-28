---
title: Rejestrowanie rozszerzeń nazw plików dla wdrożeń Side-By-Side | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- file extensions, registering for side-by-side
ms.assetid: 9ab046a2-147d-4167-aa14-7d661b1eaaa5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 996f911f37b8226065feb4da311f736dd910550b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62805990"
---
# <a name="register-file-name-extensions-for-side-by-side-deployments"></a>Rejestrowanie rozszerzeń nazw plików dla wdrożeń side-by-side
Wdrożony w środowisku side-by-side pakietów VSPackage, musisz się zarejestrować, rozszerzenia nazw plików, aby skojarzyć pliki z poprawną wersję [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Jeśli nie używasz rozszerzenia nazwy pliku określonej wersji, rejestracji umożliwia użytkownikom Otwórz swój projekt i projektu pliki elementu w odpowiedniej wersji programu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

## <a name="in-this-section"></a>W tej sekcji
- [Temat rozszerzeń nazw plików](../extensibility/about-file-name-extensions.md) w tym artykule omówiono, jak zarejestrowanych rozszerzeń nazw plików.

- [Określanie programów obsługi plików dla rozszerzeń nazw plików](../extensibility/specifying-file-handlers-for-file-name-extensions.md) zawiera informacje o sposobie rejestrowania aplikacji, które można otworzyć, edycji i tak dalej, rozszerzenie nazwy pliku określonej.

- [Rejestrowanie zleceń dla rozszerzeń nazw plików](../extensibility/registering-verbs-for-file-name-extensions.md) w tym artykule omówiono sposób rejestrowania zleceń.

- [Zarządzaj skojarzeniami plików side-by-side](../extensibility/managing-side-by-side-file-associations.md) w tym artykule omówiono sposób obsługi instalacje side-by-side, w którym konkretnej wersji [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] powinny być używane w celu otwarcia pliku.

## <a name="related-sections"></a>Sekcje pokrewne
- [Obsługę wielu wersji programu Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md) opisano problemy związane z wieloma wersjami [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] i usługi pakietu VSPackage podczas procesu projektowania i wdrażania dla użytkowników końcowych.