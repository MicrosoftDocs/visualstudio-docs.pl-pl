---
title: Rozszerzenie menu i poleceń | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- menus, common tasks
- VSPackages, menu tasks
- .vsct files, common menu tasks
ms.assetid: 7b2be4b9-e3fe-4412-874f-ae72ebc84c4b
caps.latest.revision: 50
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 83d9dc45863f1ed1b5e11c17b9e922b62b0186dc
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54803333"
---
# <a name="extending-menus-and-commands"></a>Rozszerzanie menu i poleceń
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Polecenia są sposobem dodawania akcji i procesów do programu Visual Studio. W większości przypadków polecenia są wyświetlane w menu i paski narzędzi. Szablon projektu pakietu VSPackage przedstawia sposób wdrażania wykraczającego poza podstawowe polecenia. Aby nieco dłużej, ale nadal podstawowy implementacji, zobacz [Tworzenie rozszerzenia za pomocą polecenia Menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
 Aby uzyskać więcej informacji na temat polecenia, menu i paski narzędzi programu Visual Studio, zobacz [polecenia, menu i paski narzędzi](../extensibility/internals/commands-menus-and-toolbars.md).  
  
 Polecenia, menu i paski narzędzi są zdefiniowane w pliku vsct, który jest częścią pakietu VSPackage projektów. Można znaleźć informacje o środowisku IDE programu Visual Studio i pliku vsct w [jak pakietów VSPackage dodać elementy interfejsu użytkownika](../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
 W poniższych tematach opisano sposób dodawania różne rodzaje polecenia, menu i paski narzędzi.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Dodawanie menu do paska menu programu Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)  
 Wyjaśnia, jak dodać menu na górnym pasku menu programu Visual Studio.  
  
 [Wiązanie skrótów klawiaturowych z elementami menu](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)  
 Wyjaśnia, jak dodać skrót (np. CTRL + 3) do elementu menu.  
  
 [Dodawanie podmenu do menu](../extensibility/adding-a-submenu-to-a-menu.md)  
 Wyjaśnia, jak dodawanie podmenu do menu u góry.  
  
 [Dodawanie listy ostatnio używanych elementów do podmenu](../extensibility/adding-a-most-recently-used-list-to-a-submenu.md)  
 Wyjaśnia, jak dodać listę ostatnio używanych.  
  
 [Tworzenie grup przycisków do wielokrotnego użytku](../extensibility/creating-reusable-groups-of-buttons.md)  
 W tym artykule opisano sposób grupowania elementów polecenia, tak aby mogły one zostać uwzględnione w wielu menu.  
  
 [Dodawanie ikon do poleceń menu](../extensibility/adding-icons-to-menu-commands.md)  
 Opisuje sposób dodawania ikony do polecenia na pasku narzędzi i menu.  
  
 [Zmiana tekstu polecenia menu](../extensibility/changing-the-text-of-a-menu-command.md)  
 W tym artykule opisano korzystanie z `TextChanges` flagę, aby włączyć element menu można zmieniać dynamicznie.  
  
 [Zmiana wyglądu polecenia](../extensibility/changing-the-appearance-of-a-command.md)  
 Opisuje sposób dynamiczne Włączanie lub wyłączanie polecenia.  
  
 [Aktualizowanie interfejsu użytkownika](../extensibility/updating-the-user-interface.md)  
 W tym artykule opisano sposób wymusić aktualizację interfejsu użytkownika w celu odzwierciedlenia ostatnich zmian.  
  
 [Lokalizowanie poleceń menu](../extensibility/localizing-menu-commands.md)  
 Wyjaśnia, jak lokalizowanie poleceń menu.  
  
## <a name="related-sections"></a>Sekcje pokrewne
