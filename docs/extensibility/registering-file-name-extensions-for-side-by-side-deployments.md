---
title: Rejestrowanie rozszerzeń nazw plików dla środowisk IDE równoległych
description: Dowiedz się więcej o rejestrowaniu rozszerzeń nazw plików dla wdrożeń równoległych, co umożliwia użytkownikom otwieranie plików w odpowiedniej wersji programu Visual Studio.
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
ms.openlocfilehash: c66413890f0aaa08e09a291f5bf31a44e7c24706
ms.sourcegitcommit: dd96a95d87a039525aac86abe689c30e2073ae87
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/04/2021
ms.locfileid: "97863027"
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
