---
title: Obsługa wielu wersji programu Visual Studio 2015 | Microsoft Docs
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, supporting multiple versions
- VSPackages, side-by-side compatibility
ms.assetid: 0047aa90-1ed4-40d3-8772-622b2719a4b1
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8f4393a88a689e2a923291ada37a9b6d85718db5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64779415"
---
# <a name="supporting-multiple-versions-of-visual-studio"></a>Obsługiwanie wielu wersji programu Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Termin *równoczesny* oznacza, że można zainstalować i zachować wiele wersji produktu na tym samym komputerze. W przypadku pakietów VSPackage oznacza, że użytkownik może mieć kilka wersji programu Visual Studio zainstalowanych na tym samym komputerze. Nie można jednak korzystać ze równoległych wersji pakietów VSPackage załadowanych w jednej wersji programu Visual Studio.

 Przed udostępnieniem pakietu VSPackage można załadować do kolejnych wersji programu Visual Studio, weź pod uwagę następujące kwestie:

- Należy określić, którą strategię implementacji obok siebie chcesz wykonać.

     Aby uzyskać więcej informacji, zobacz [Wybieranie między udostępnionymi a wersjami pakietów VSPackage](../extensibility/choosing-between-shared-and-versioned-vspackages.md).

- Twoje rozwiązanie i formaty plików projektu muszą pasować do strategii implementacji.

     Aby uzyskać więcej informacji, zobacz [uaktualnianie projektów niestandardowych](../misc/upgrading-custom-projects.md) i [Rejestrowanie rozszerzeń nazw plików dla wdrożeń równoległych](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md).

- Instalator musi obsłużyć strategię implementacji, aby składniki wersji, a także składniki udostępnione dla wszystkich wersji, były poprawnie zainstalowane i zarejestrowane.

     Aby uzyskać więcej informacji, zobacz [Installing pakietów VSPackage With Instalator Windows](../extensibility/internals/installing-vspackages-with-windows-installer.md) , a także [Zarządzanie składnikami](../extensibility/internals/component-management.md).

    > [!NOTE]
    > Zainstalowanie wersji programu Visual Studio powoduje także zainstalowanie odpowiedniej wersji programu [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] . Na przykład zainstalowanie programu Visual Studio 2010 i programu Visual Studio 2012 na tym samym komputerze powoduje także zainstalowanie odpowiednio wersji 4,0 i 4,5 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] .

## <a name="in-this-section"></a>W tej sekcji
 [Wybieranie między udostępnionym i z wersją pakietów VSPackage](../extensibility/choosing-between-shared-and-versioned-vspackages.md) Wyjaśniono, jak rozwiązywać problemy obok siebie w pakietu VSPackage.

 [Rejestrowanie rozszerzeń nazw plików dla wdrożeń równoległych](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md) Opisuje, w jaki sposób pakietu VSPackage może rejestrować skojarzenia plików w scenariuszu równoległym.

## <a name="related-sections"></a>Sekcje pokrewne
 [Instalowanie pakietów VSPackage](../misc/installing-vspackages.md) W tym artykule omówiono sposób kompilowania i instalowania pakietów VSPackage oraz obsługi użytkowników, którzy uruchamiali wiele wersji programu Visual Studio w tym samym czasie.
