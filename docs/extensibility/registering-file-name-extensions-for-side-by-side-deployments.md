---
title: Rejestrowanie rozszerzeń nazw plików dla wdrożeń side-by-side | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- file extensions, registering for side-by-side
ms.assetid: 9ab046a2-147d-4167-aa14-7d661b1eaaa5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6717625a44b48a25d293f68d01cd9fa3c7c24853
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701544"
---
# <a name="register-file-name-extensions-for-side-by-side-deployments"></a>Rejestrowanie rozszerzeń nazw plików dla wdrożeń side-by-side
W przypadku pakietów VSPackages wdrożonych w środowisku side-by-side należy zarejestrować rozszerzenia [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]nazw plików, aby skojarzyć pliki z poprawną wersją programu . O ile nie jest używane rozszerzenie nazwy pliku specyficzne dla wersji, rejestracja umożliwia [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]użytkownikom otwieranie plików elementów projektu i projektu w odpowiedniej wersji programu .

## <a name="in-this-section"></a>W tej sekcji
- [Rozszerzenia nazw plików – informacje](../extensibility/about-file-name-extensions.md) W tym artykule omówiono sposób rejestrowania rozszerzeń nazw plików.

- [Określanie programów obsługi plików dla rozszerzeń nazw plików](../extensibility/specifying-file-handlers-for-file-name-extensions.md) Zawiera informacje dotyczące rejestrowania aplikacji, które mogą otwierać, edytować i tak dalej, rozszerzenie nazwy określonego pliku.

- [Rejestrowanie zleceń dla rozszerzeń nazw plików](../extensibility/registering-verbs-for-file-name-extensions.md) W tym artykule omówiono sposób rejestrowania zleceń.

- [Zarządzanie skojarzeniami plików obok siebie](../extensibility/managing-side-by-side-file-associations.md) W tym artykule omówiono sposób obsługi instalacji side-by-side, w których [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] należy wywołać określoną wersję, aby otworzyć plik.

## <a name="related-sections"></a>Powiązane sekcje
- [Obsługa wielu wersji programu Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md) W tym artykule [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] opisano problemy związane z wieloma wersjami i VSPackage podczas tworzenia i wdrażania dla użytkowników końcowych.
