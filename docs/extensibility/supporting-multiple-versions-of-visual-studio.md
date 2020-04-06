---
title: Obsługa wielu wersji programu Visual Studio | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, supporting multiple versions
- VSPackages, side-by-side compatibility
ms.assetid: 0047aa90-1ed4-40d3-8772-622b2719a4b1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1d571f1be4da45ff5ed6b2538cfb515930bde1de
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699473"
---
# <a name="supporting-multiple-versions-of-visual-studio"></a>Obsługiwanie wielu wersji programu Visual Studio
Termin *side-by-side* oznacza, że można zainstalować i obsługiwać wiele wersji produktu na tym samym komputerze. Dla vsPackages oznacza to, że użytkownik może mieć kilka wersji programu Visual Studio zainstalowanych na tym samym komputerze. Jednak nie można mieć side-by-side wersje vspackages załadowany do jednej wersji programu Visual Studio.

 Przed udostępnieniem pakietu VSPackage do wersji obok siebie programu Visual Studio należy wziąć pod uwagę następujące kwestie:

- Należy określić, którą strategię wdrażania side-by-side chcesz wykonać.

   Aby uzyskać więcej informacji, zobacz [Wybieranie między pakietami współdzielonymi i wersjonowanymi pakietami VSPackages](../extensibility/choosing-between-shared-and-versioned-vspackages.md).

- Formaty plików rozwiązania i projektu muszą być zgodne ze strategią wdrażania.

   Aby uzyskać więcej informacji, zobacz [Uaktualnianie projektów niestandardowych](../extensibility/internals/upgrading-projects.md#upgrading-custom-projects) i [rejestrowanie rozszerzeń nazw plików dla wdrożeń obok siebie](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md).

- Instalator musi obsługiwać strategię implementacji, tak aby składniki wersjonowane, a także składniki współużytkowane we wszystkich wersjach, zostały poprawnie zainstalowane i zarejestrowane.

   Aby uzyskać więcej informacji, zobacz [Instalowanie pakietów VSPackages z Instalatorem Windows,](../extensibility/internals/installing-vspackages-with-windows-installer.md) a także [zarządzanie składnikami](../extensibility/internals/component-management.md).

  > [!NOTE]
  > Instalowanie wersji programu Visual Studio instaluje również odpowiednią wersję programu .NET Framework. Na przykład instalowanie programu Visual Studio 2010 i Visual Studio 2012 na tym samym komputerze również instaluje wersje 4.0 i 4.5 programu .NET Framework, odpowiednio.

## <a name="in-this-section"></a>W tej sekcji
- [Wybieranie między pakietami współdzielonymi i wersjonowanymi pakietami VSPackage](../extensibility/choosing-between-shared-and-versioned-vspackages.md) W tym artykule wyjaśniono, jak rozwiązać problemy side-by-side w vspackage.

- [Rejestrowanie rozszerzeń nazw plików dla wdrożeń side-by-side](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md) W tym artykule opisano, jak vspackage można zarejestrować skojarzenia plików w scenariuszu side-by-side.

## <a name="related-sections"></a>Sekcje pokrewne
- [Instalowanie pakietów VSPackage przy użyciu Instalatora Windows](../extensibility/internals/installing-vspackages-with-windows-installer.md)
