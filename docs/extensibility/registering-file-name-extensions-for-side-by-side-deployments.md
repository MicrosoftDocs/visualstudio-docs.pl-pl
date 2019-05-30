---
title: Rejestrowanie rozszerzeń nazw plików dla wdrożeń Side-By-Side | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- file extensions, registering for side-by-side
ms.assetid: 9ab046a2-147d-4167-aa14-7d661b1eaaa5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9bdfb562ddfcce2584b8868c3c931c21f9dbc127
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66334232"
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