---
title: Obsługiwanie wielu wersji programu Visual Studio | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, supporting multiple versions
- VSPackages, side-by-side compatibility
ms.assetid: 0047aa90-1ed4-40d3-8772-622b2719a4b1
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f7212445cd507a0d7d185bbd73fa2292e5b783f4
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2019
ms.locfileid: "66745989"
---
# <a name="supporting-multiple-versions-of-visual-studio"></a>Obsługiwanie wielu wersji programu Visual Studio
Termin *side-by-side* oznacza, że można zainstalować i zarządzać wieloma wersjami produktu na tym samym komputerze. Dla pakietów VSPackage oznacza to, że użytkownik może mieć różne wersje programu Visual Studio zainstalowany na tym samym komputerze. Jednak nie może mieć side-by-side wersje usługi pakietów VSPackage załadowane do jednej wersji programu Visual Studio.

 Przed wprowadzeniem Twojego pakietu VSPackage, mogą być ładowane do side-by-side wersji programu Visual Studio, należy rozważyć następujące kwestie:

- Należy ustalić strategię wdrażania side-by-side, w jakiej chcesz obserwować.

   Aby uzyskać więcej informacji, zobacz [wybór między udostępnionych i kontrolą wersji pakietów VSPackage](../extensibility/choosing-between-shared-and-versioned-vspackages.md).

- Formaty plików rozwiązania i projektu należy dopasować strategii wdrażania.

   Aby uzyskać więcej informacji, zobacz [Uaktualnianie projektów niestandardowych](../extensibility/internals/upgrading-projects.md#upgrading-custom-projects) i [rejestrowanie rozszerzeń nazw plików dla wdrożeń Side-By-Side](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md).

- Instalatora musi obsługiwać swoją strategię wdrażania, aby składniki numerów wersji, a także składniki współużytkowane przez wszystkie wersje, są poprawnie zainstalowane i zarejestrowane.

   Aby uzyskać więcej informacji, zobacz [instalowanie pakietów VSPackage przy użyciu Instalatora Windows](../extensibility/internals/installing-vspackages-with-windows-installer.md) , a także [Zarządzanie składnikami](../extensibility/internals/component-management.md).

  > [!NOTE]
  > Instalowanie wersji programu Visual Studio instaluje odpowiednią wersję programu .NET Framework. Na przykład instalacji programu Visual Studio 2010 i Visual Studio 2012 na tym samym komputerze również zostanie zainstalowany w wersji 4.0 i 4.5 programu .NET Framework, odpowiednio.

## <a name="in-this-section"></a>W tej sekcji
- [Wybór między udostępnionych i kontrolą wersji pakietów VSPackage](../extensibility/choosing-between-shared-and-versioned-vspackages.md) wyjaśnia, jak rozwiązywać problemy side-by-side w swojej pakietu VSPackage.

- [Rejestrowanie rozszerzeń nazw plików dla wdrożeń Side-By-Side](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md) w tym artykule opisano, jak zarejestrować skojarzenia plików w scenariuszu side-by-side Twojego pakietu VSPackage.

## <a name="related-sections"></a>Sekcje pokrewne
- [Instalowanie pakietów VSPackage przy użyciu Instalatora Windows](../extensibility/internals/installing-vspackages-with-windows-installer.md)
