---
title: Rejestrowanie rozszerzeń nazw plików dla środowisk IDE równoległych
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: c5ebedd2861ca96d1ad96c74a54da06578d33960
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2020
ms.locfileid: "90036954"
---
# <a name="register-file-name-extensions-for-side-by-side-deployments"></a>Rejestrowanie rozszerzeń nazw plików dla wdrożeń równoległych
W przypadku pakietów VSPackage wdrożonych w środowisku Side-by-Side należy zarejestrować rozszerzenia nazw plików w celu kojarzenia plików z poprawną wersją programu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Jeśli nie zostanie użyte rozszerzenie nazwy pliku specyficznego dla wersji, rejestracja umożliwia użytkownikom otwieranie plików projektu i elementów projektu w odpowiedniej wersji programu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

## <a name="in-this-section"></a>W tej sekcji
- [Informacje o rozszerzeniach nazw plików](../extensibility/about-file-name-extensions.md) W tym artykule omówiono sposób rejestrowania rozszerzeń nazw plików.

- [Określ programy obsługi plików dla rozszerzeń nazw plików](../extensibility/specifying-file-handlers-for-file-name-extensions.md) Zawiera informacje dotyczące sposobu rejestrowania aplikacji, które mogą otwierać, edytować i tak dalej, w przypadku konkretnego rozszerzenia nazwy pliku.

- [Rejestrowanie czasowników dla rozszerzeń nazw plików](../extensibility/registering-verbs-for-file-name-extensions.md) W tym artykule omówiono sposób rejestrowania zleceń.

- [Zarządzaj skojarzeniami plików obok](../extensibility/managing-side-by-side-file-associations.md) siebie W tym artykule omówiono sposób obsługi instalacji równoległych, w których należy wywołać konkretną wersję programu, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Aby otworzyć plik.

## <a name="related-sections"></a>Sekcje pokrewne
- [Obsługa wielu wersji programu Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md) W tym artykule opisano problemy związane z wieloma wersjami [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] i pakietu VSPackage podczas opracowywania i wdrażania dla użytkowników końcowych.
