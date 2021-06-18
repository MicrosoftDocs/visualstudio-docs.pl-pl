---
title: AutoRecover, środowisko, opcje — Okno dialogowe
description: Dowiedz się więcej o oknie dialogowym AutoOdzyskowanie, Środowisko, Opcje i o tym, jak jest ono używane do określania, czy mają być automatycznie tworzone pliki kopii zapasowej.
ms.custom: SEO-VS-2020
ms.date: 08/14/2020
ms.topic: reference
f1_keywords:
- VS.DialogAutoRestore
- VS.ToolsOptionsPages.Environment.AutoRecover
- VS.ToolsOptionsPages.Environment.Auto_Save_and_Restore
helpviewer_keywords:
- files, recovering
- AutoRecover page
- saving files, automatically
- files, saving automatically
ms.assetid: 397e5e44-4bbe-4289-94d1-642b466c9111
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 007e82ee7c1c2839ba266794432605f1f92a1669
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2021
ms.locfileid: "112307794"
---
# <a name="autorecover-environment-options-dialog-box"></a>AutoOdzyskowanie, Środowisko, Opcje — okno dialogowe

Użyj tej strony w **oknie dialogowym** Opcje, aby określić, czy mają być automatycznie tworzone pliki kopii zapasowej. Możesz również określić, czy chcesz przywrócić zmodyfikowane pliki, jeśli Visual Studio zostanie nieoczekiwanie zamknięty.

Aby uzyskać dostęp do tego okna dialogowego, przejdź do **opcji**  >  **narzędzia**  >  **Środowiska**  >  **autoodzysk.**

:::image type="content" source="media/autorecover-options.png" alt-text="Zrzut ekranu przedstawiający sekcję AutoOdzysłanie w oknie dialogowym Opcje":::

**Zapisywanie informacji autoodzyskowania co [n] minut**

::: moniker range=">=vs-2022"

Ta opcja umożliwia dostosowanie, jak często plik jest automatycznie zapisywany w edytorze. W przypadku wcześniej zapisanych plików Visual Studio kopię pliku w folderze ***%LocalAppData%\Microsoft\VisualStudio\BackupFiles \\ [nazwa_projektu]***. Jeśli plik jest nowy i nie został jeszcze zapisany, Visual Studio automatycznie go przy użyciu losowo wygenerowanej nazwy pliku.

::: moniker-end

::: moniker range="vs-2019"

Ta opcja umożliwia dostosowanie, jak często plik jest automatycznie zapisywany w edytorze. W przypadku wcześniej zapisanych plików program Visual Studio 2019 w wersji 16.2 lub nowszej zapisuje kopię pliku w folderze ***%LocalAppData%\Microsoft\VisualStudio\BackupFiles \\ [nazwa_projektu]***. Jeśli plik jest nowy i nie został jeszcze zapisany, Visual Studio automatycznie go przy użyciu losowo wygenerowanej nazwy pliku.

> [!NOTE]
> Jeśli używasz programu Visual Studio 2019 w wersji 16.1 lub starszej, lokalizacja pliku to *%USERPROFILE%\Documents\Visual Studio [wersja]\Backup Files \\ [nazwa_projektu]*. Aby uzyskać więcej informacji, zobacz [stronę Visual Studio 2019 Release Notes History (Historia](/visualstudio/releases/2019/release-notes-history/) informacji o wersji 2019).

::: moniker-end

::: moniker range="vs-2017"

Ta opcja umożliwia dostosowanie, jak często plik jest automatycznie zapisywany w edytorze. W przypadku wcześniej zapisanych plików program Visual Studio 2017 zapisuje kopię pliku w folderze *%USERPROFILE%\Documents\Visual Studio [wersja]\Backup Files \\ [nazwa_projektu]*. Jeśli plik jest nowy i nie został jeszcze zapisany, Visual Studio automatycznie go przy użyciu losowo wygenerowanej nazwy pliku.

::: moniker-end

**Zachowaj informacje o funkcji AutoRecover przez [n] dni**

Użyj tej opcji, aby określić, jak długo Visual Studio pliki utworzone na użytek automatycznego przekierowania.

### <a name="see-also"></a>Zobacz też

- [Opcje — Okno dialogowe](../../ide/reference/options-dialog-box-visual-studio.md)
