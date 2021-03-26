---
title: Rejestrowanie rozszerzeń nazw plików dla środowisk IDE równoległych
description: Dowiedz się więcej o rejestrowaniu rozszerzeń nazw plików dla wdrożeń równoległych, co umożliwia użytkownikom otwieranie plików w odpowiedniej wersji programu Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- file extensions, registering for side-by-side
ms.assetid: 9ab046a2-147d-4167-aa14-7d661b1eaaa5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ad6b5715b767729715403d064cd46b4556fa17e3
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105056561"
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
