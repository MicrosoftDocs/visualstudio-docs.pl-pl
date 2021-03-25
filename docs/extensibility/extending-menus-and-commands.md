---
title: Rozszerzanie menu i poleceń | Microsoft Docs
description: Informacje o poleceniach, które dodają akcje i procesy do programu Visual Studio. Szablon projektu pakietu VSPackage pokazuje, jak zaimplementować bardzo podstawowe polecenie.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- menus, common tasks
- VSPackages, menu tasks
- .vsct files, common menu tasks
ms.assetid: 7b2be4b9-e3fe-4412-874f-ae72ebc84c4b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6a96978cdad45c669b607c18e12b2e492dcf95bb
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105075214"
---
# <a name="extend-menus-and-commands"></a>Poszerzanie menu i poleceń
Polecenia służą do dodawania akcji i procesów do programu Visual Studio. W większości przypadków polecenia są wyświetlane w menu lub paskach narzędzi. Szablon projektu pakietu VSPackage pokazuje, jak zaimplementować bardzo podstawowe polecenie. Aby uzyskać nieco więcej, ale nadal podstawową implementację, zobacz [Tworzenie rozszerzenia za pomocą polecenia menu](../extensibility/creating-an-extension-with-a-menu-command.md).

 Aby uzyskać więcej informacji na temat poleceń, menu i pasków narzędzi programu Visual Studio, zobacz [polecenia, menu i paski narzędzi](../extensibility/internals/commands-menus-and-toolbars.md).

 Polecenia, menu i paski narzędzi są zdefiniowane w pliku *vsct* , który jest częścią projektów pakietu VSPackage. Informacje na temat środowiska IDE programu Visual Studio i pliku *. vsct* można znaleźć w temacie [pakietów VSPackage Dodawanie elementów interfejsu użytkownika](../extensibility/internals/how-vspackages-add-user-interface-elements.md).

 W poniższych tematach opisano, jak dodawać różne rodzaje poleceń, menu i paski narzędzi.

## <a name="in-this-section"></a>W tej sekcji
- [Dodawanie menu do paska menu programu Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) Wyjaśnia, jak dodać menu do górnego paska menu programu Visual Studio.

- [Powiąż skróty klawiaturowe z elementami menu](../extensibility/binding-keyboard-shortcuts-to-menu-items.md) Wyjaśnia, jak dodać skrót klawiaturowy (taki jak CTRL + 3) do elementu menu.

- [Dodawanie podmenu do menu](../extensibility/adding-a-submenu-to-a-menu.md) Wyjaśnia, jak dodać podmenu do górnego menu.

- [Dodaj ostatnio używaną listę do podmenu](../extensibility/adding-a-most-recently-used-list-to-a-submenu.md) Wyjaśnia, jak dodać ostatnio używaną listę.

- [Tworzenie grup przycisków do wielokrotnego użytku](../extensibility/creating-reusable-groups-of-buttons.md) Opisuje sposób grupowania elementów poleceń tak, aby mogły być zawarte w wielu menu.

- [Dodawanie ikon do poleceń menu](../extensibility/adding-icons-to-menu-commands.md) Opisuje sposób dodawania ikony do polecenia na pasku narzędzi i w menu.

- [Zmiana tekstu polecenia menu](../extensibility/changing-the-text-of-a-menu-command.md) Opisuje użycie `TextChanges` flagi, aby umożliwić dynamiczną zmianę elementu menu.

- [Zmiana wyglądu polecenia](../extensibility/changing-the-appearance-of-a-command.md) Opisuje sposób dynamicznego włączania lub wyłączania polecenia.

- [Aktualizowanie interfejsu użytkownika](../extensibility/updating-the-user-interface.md) Opisuje, jak wymusić aktualizację interfejsu użytkownika w celu odzwierciedlenia najnowszych zmian.

- [Lokalizowanie poleceń menu](../extensibility/localizing-menu-commands.md) Wyjaśnia sposób lokalizowania poleceń menu.
