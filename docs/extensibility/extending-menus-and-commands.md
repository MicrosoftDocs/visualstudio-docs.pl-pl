---
title: Rozszerzenie menu i poleceń | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- menus, common tasks
- VSPackages, menu tasks
- .vsct files, common menu tasks
ms.assetid: 7b2be4b9-e3fe-4412-874f-ae72ebc84c4b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c8f8d98525f1038b4a50dcaa5ca6237bd4c0f7b5
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56709268"
---
# <a name="extend-menus-and-commands"></a>Rozszerzenie menu i poleceń
Polecenia są sposobem dodawania akcji i procesów do programu Visual Studio. W większości przypadków polecenia są wyświetlane w menu i paski narzędzi. Szablon projektu pakietu VSPackage przedstawia sposób wdrażania wykraczającego poza podstawowe polecenia. Aby nieco dłużej, ale nadal podstawowy implementacji, zobacz [Tworzenie rozszerzenia za pomocą polecenia menu](../extensibility/creating-an-extension-with-a-menu-command.md).

 Aby uzyskać więcej informacji na temat polecenia, menu i paski narzędzi programu Visual Studio, zobacz [polecenia, menu i paski narzędzi](../extensibility/internals/commands-menus-and-toolbars.md).

 Polecenia, menu i paski narzędzi, które są zdefiniowane w *vsct* pliku częścią pakietu VSPackage projektów. Można znaleźć informacje o środowisku IDE programu Visual Studio i *vsct* w pliku [VSPackages jak dodać elementy interfejsu użytkownika](../extensibility/internals/how-vspackages-add-user-interface-elements.md).

 W poniższych tematach opisano sposób dodawania różne rodzaje polecenia, menu i paski narzędzi.

## <a name="in-this-section"></a>W tej sekcji
- [Dodawanie menu na pasku menu programu Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) wyjaśnia, jak dodać menu na górnym pasku menu programu Visual Studio.

- [Powiąż skrótów klawiaturowych z elementami menu](../extensibility/binding-keyboard-shortcuts-to-menu-items.md) został objaśniony sposób dodawania (np. CTRL + 3) skrót klawiaturowy do elementu menu.

- [Dodawanie podmenu do menu](../extensibility/adding-a-submenu-to-a-menu.md) wyjaśnia, jak dodawanie podmenu do menu u góry.

- [Dodawanie listy ostatnio używanych elementów do podmenu](../extensibility/adding-a-most-recently-used-list-to-a-submenu.md) wyjaśnia, jak dodać listę ostatnio używanych.

- [Tworzenie grup do ponownego użycia przycisków](../extensibility/creating-reusable-groups-of-buttons.md) w tym artykule opisano sposób grupowania elementów polecenia, tak aby mogły one zostać uwzględnione w wielu menu.

- [Dodawanie ikon do poleceń menu](../extensibility/adding-icons-to-menu-commands.md) opisano, jak dodać ikonę polecenie na pasku narzędzi i menu.

- [Zmiana tekstu polecenia menu](../extensibility/changing-the-text-of-a-menu-command.md) opisuje korzystanie z `TextChanges` flagę, aby włączyć element menu można zmieniać dynamicznie.

- [Zmiana wyglądu polecenia](../extensibility/changing-the-appearance-of-a-command.md) opisano, jak dynamicznie włączać lub wyłączać polecenia.

- [Zaktualizuj interfejs użytkownika](../extensibility/updating-the-user-interface.md) w tym artykule opisano sposób wymusić aktualizację interfejsu użytkownika w celu odzwierciedlenia ostatnich zmian.

- [Lokalizowanie poleceń menu](../extensibility/localizing-menu-commands.md) wyjaśnia, jak lokalizowanie poleceń menu.