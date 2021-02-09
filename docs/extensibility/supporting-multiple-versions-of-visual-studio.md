---
title: Obsługa wielu wersji programu Visual Studio | Microsoft Docs
description: Dowiedz się, w jaki sposób można obsługiwać kilka wersji programu Visual Studio, dzięki którym pakietów VSPackage można ładować do różnych wersji.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, supporting multiple versions
- VSPackages, side-by-side compatibility
ms.assetid: 0047aa90-1ed4-40d3-8772-622b2719a4b1
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 52b8bf1be57e10790d91d4712e56d707621cc7df
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99889944"
---
# <a name="supporting-multiple-versions-of-visual-studio"></a>Obsługiwanie wielu wersji programu Visual Studio
Termin *równoczesny* oznacza, że można zainstalować i zachować wiele wersji produktu na tym samym komputerze. W przypadku pakietów VSPackage oznacza, że użytkownik może mieć kilka wersji programu Visual Studio zainstalowanych na tym samym komputerze. Nie można jednak korzystać ze równoległych wersji pakietów VSPackage załadowanych w jednej wersji programu Visual Studio.

 Przed udostępnieniem pakietu VSPackage można załadować do kolejnych wersji programu Visual Studio, weź pod uwagę następujące kwestie:

- Należy określić, którą strategię implementacji obok siebie chcesz wykonać.

   Aby uzyskać więcej informacji, zobacz [Wybieranie między udostępnionymi a wersjami pakietów VSPackage](../extensibility/choosing-between-shared-and-versioned-vspackages.md).

- Twoje rozwiązanie i formaty plików projektu muszą pasować do strategii implementacji.

   Aby uzyskać więcej informacji, zobacz [uaktualnianie projektów niestandardowych](../extensibility/internals/upgrading-projects.md#upgrading-custom-projects) i [Rejestrowanie rozszerzeń nazw plików dla wdrożeń równoległych](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md).

- Instalator musi obsłużyć strategię implementacji, aby składniki wersji, a także składniki udostępnione dla wszystkich wersji, były poprawnie zainstalowane i zarejestrowane.

   Aby uzyskać więcej informacji, zobacz [Installing pakietów VSPackage With Instalator Windows](../extensibility/internals/installing-vspackages-with-windows-installer.md) , a także [Zarządzanie składnikami](../extensibility/internals/component-management.md).

  > [!NOTE]
  > Zainstalowanie wersji programu Visual Studio powoduje także zainstalowanie odpowiedniej wersji .NET Framework. Na przykład zainstalowanie programu Visual Studio 2010 i programu Visual Studio 2012 na tym samym komputerze powoduje także zainstalowanie odpowiednio wersji 4,0 i 4,5 .NET Framework.

## <a name="in-this-section"></a>W tej sekcji
- [Wybieranie między udostępnionym i z wersją pakietów VSPackage](../extensibility/choosing-between-shared-and-versioned-vspackages.md) Wyjaśniono, jak rozwiązywać problemy obok siebie w pakietu VSPackage.

- [Rejestrowanie rozszerzeń nazw plików dla wdrożeń równoległych](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md) Opisuje, w jaki sposób pakietu VSPackage może rejestrować skojarzenia plików w scenariuszu równoległym.

## <a name="related-sections"></a>Sekcje pokrewne
- [Instalowanie pakietów VSPackage przy użyciu Instalatora Windows](../extensibility/internals/installing-vspackages-with-windows-installer.md)
