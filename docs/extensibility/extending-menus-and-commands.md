---
title: Rozszerzanie menu i poleceń | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- menus, common tasks
- VSPackages, menu tasks
- .vsct files, common menu tasks
ms.assetid: 7b2be4b9-e3fe-4412-874f-ae72ebc84c4b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dfcedd3f1b4cb48631541f1726556dab766402ab
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711797"
---
# <a name="extend-menus-and-commands"></a>Rozszerzanie menu i poleceń
Polecenia są sposobem dodawania akcji i procesów do programu Visual Studio. W większości przypadków polecenia są wyświetlane w menu lub na paskach narzędzi. Szablon projektu VSPackage pokazuje, jak zaimplementować bardzo podstawowe polecenie. Aby uzyskać nieco dłuższą, ale nadal [podstawową](../extensibility/creating-an-extension-with-a-menu-command.md)implementację, zobacz Tworzenie rozszerzenia za pomocą polecenia menu .

 Aby uzyskać więcej informacji na temat poleceń programu Visual Studio, menu i pasków narzędzi, zobacz [Polecenia, menu i paski narzędzi](../extensibility/internals/commands-menus-and-toolbars.md).

 Polecenia, menu i paski narzędzi są zdefiniowane w pliku *vsct,* który jest częścią projektów VSPackage. Informacje na temat ide programu Visual Studio i pliku *vsct* można znaleźć w programie [Jak vsPackages dodają elementy interfejsu użytkownika.](../extensibility/internals/how-vspackages-add-user-interface-elements.md)

 W poniższych tematach wyjaśniono, jak dodać różne rodzaje poleceń, menu i pasków narzędzi.

## <a name="in-this-section"></a>W tej sekcji
- [Dodawanie menu do paska menu programu Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) W tym artykule wyjaśniono, jak dodać menu do górnego paska menu programu Visual Studio.

- [Powiązuj skróty klawiaturowe z elementami menu](../extensibility/binding-keyboard-shortcuts-to-menu-items.md) W tym artykule wyjaśniono, jak dodać skrót klawiaturowy (na przykład CTRL + 3) do elementu menu.

- [Dodawanie podmenu do menu](../extensibility/adding-a-submenu-to-a-menu.md) W tym artykule wyjaśniono, jak dodać podmenu do górnego menu.

- [Dodawanie ostatnio używanej listy do podmenu](../extensibility/adding-a-most-recently-used-list-to-a-submenu.md) W tym artykule wyjaśniono, jak dodać listę ostatnio używane.

- [Tworzenie grup przycisków wielokrotnego pożyciem](../extensibility/creating-reusable-groups-of-buttons.md) W tym artykule opisano sposób grupowanie elementów poleceń, tak aby mogły być uwzględniane w wielu menu.

- [Dodawanie ikon do poleceń menu](../extensibility/adding-icons-to-menu-commands.md) W tym artykule opisano sposób dodawania ikony do polecenia zarówno na pasku narzędzi, jak i w menu.

- [Zmienianie tekstu polecenia menu](../extensibility/changing-the-text-of-a-menu-command.md) W tym artykule opisano użycie flagi, `TextChanges` aby włączyć element menu, które mają być zmieniane dynamicznie.

- [Zmienianie wyglądu polecenia](../extensibility/changing-the-appearance-of-a-command.md) W tym artykule opisano sposób dynamicznego włączania lub wyłączania polecenia.

- [Aktualizowanie interfejsu użytkownika](../extensibility/updating-the-user-interface.md) W tym artykule opisano, jak wymusić aktualizację interfejsu użytkownika, aby odzwierciedlić ostatnie zmiany.

- [Lokalizowanie poleceń menu](../extensibility/localizing-menu-commands.md) W tym artykule wyjaśniono, jak zlokalizować polecenia menu.
