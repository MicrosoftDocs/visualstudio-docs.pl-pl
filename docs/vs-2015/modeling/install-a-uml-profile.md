---
title: Instalowanie profilu UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML - extending, profiles
ms.assetid: 586f9ba5-4d01-4a1d-b001-32e2efaa4f24
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 89531fe0f2e912a6aabd962ab56ca7a24a7f3e20
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2020
ms.locfileid: "75850663"
---
# <a name="install-a-uml-profile"></a>Instalowanie profilu UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Program Visual Studio można rozszerzyć przy użyciu profilu UML. Profil umożliwia dodanie stereotypów i dodatkowych właściwości do elementów, które można utworzyć w modelach UML. Aby sprawdzić, które wersje programu Visual Studio obsługują tę funkcję, zobacz [Obsługa wersji dla narzędzi architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 Jeśli zostanie wyświetlony model UML, który został utworzony za pomocą profilów, niektóre właściwości nie będą wyświetlane, chyba że zostaną zainstalowane te same profile.

 Profil jest dystrybuowany wewnątrz rozszerzenia programu Visual Studio. Rozszerzenie może również zawierać inne funkcje, takie jak polecenia menu. Aby uzyskać więcej informacji, zobacz [Zarządzanie rozszerzeniami programu Visual Studio](https://msdn.microsoft.com/library/dd293638(VS.100).aspx).

### <a name="to-install-a-uml-profile-on-your-computer"></a>Aby zainstalować profil UML na komputerze

1. Profil powinien zostać udzielony w postaci pliku rozszerzenia programu Visual Studio (`.vsix`). Mogą istnieć inne funkcje w tym samym pliku.

     Przenieś plik `.vsix` do wygodnej lokalizacji na komputerze.

2. Kliknij dwukrotnie plik `.vsix` w Eksploratorze Windows (lub Eksploratorze plików) lub Otwórz go w programie [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].

3. Kliknij przycisk **Instaluj** w wyświetlonym oknie dialogowym.

4. Aby odinstalować lub tymczasowo wyłączyć rozszerzenie, Otwórz **Menedżera rozszerzeń** z menu **Narzędzia** .

### <a name="to-uninstall-or-disable-a-profile-extension"></a>Aby odinstalować lub wyłączyć rozszerzenie profilu

1. W menu **Narzędzia** programu Visual Studio kliknij pozycję **Menedżer rozszerzeń**.

2. Kliknij rozszerzenie, które chcesz usunąć, a następnie kliknij przycisk **Wyłącz** lub **Odinstaluj**.

## <a name="see-also"></a>Zobacz też
 [Dostosowywanie modelu za pomocą profilów i stereotypów](../modeling/customize-your-model-with-profiles-and-stereotypes.md) [Zdefiniuj profil, aby zwiększyć UML](../modeling/define-a-profile-to-extend-uml.md)
