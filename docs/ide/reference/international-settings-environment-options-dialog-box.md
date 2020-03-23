---
title: Ustawienia międzynarodowe, środowisko, opcje — Okno dialogowe
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Environment.InternationalSettings
- VS.ToolsOptionsPages.Environment.International_Settings
- VS.Environment.International Settings
helpviewer_keywords:
- International Settings dialog box
- languages, environment settings
- Options dialog box, international settings
- languages, specifying default
ms.assetid: e3a8815c-6995-4099-8e88-34f91fad55b2
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1526e1c49636f4883392caa63966714625d066d6
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595517"
---
# <a name="options-dialog-box-environment--international-settings"></a>Okno dialogowe \> Opcje: Ustawienia międzynarodowe środowiska

Strona Ustawienia międzynarodowe umożliwia zmianę języka domyślnego, gdy na komputerze jest zainstalowanych więcej niż jedną wersję językową zintegrowanego środowiska programistycznego (IDE). Dostęp do tego okna dialogowego można uzyskać, wybierając **polecenie Opcje** z menu **Narzędzia,** a następnie wybierając pozycję **Ustawienia międzynarodowe** z folderu **Środowisko.**

**Język**

Wyświetla listę dostępnych języków dla zainstalowanych wersji językowych produktu. Jeśli środowisko współużytkuje wiele języków produktów lub instalację w języku mieszanym produktów, wybór języka zostanie zmieniony na **Taki sam jak system Microsoft Windows**.

> [!CAUTION]
> W systemie z zainstalowanymi wieloma językami to ustawienie nie ma wpływu na narzędzia kompilacji języka Visual C++ (cl.exe, link.exe, nmake.exe, bscmake.exe i powiązane pliki). Narzędzia te używają wersji dla ostatniego zainstalowanego języka. Narzędzia kompilacji dla wcześniej zainstalowanego języka są zastępowane, ponieważ narzędzia kompilacji visual C++ nie używają modelu biblioteki DLL satelitarnej.

### <a name="see-also"></a>Zobacz też

- [Instalowanie pakietów językowych](../../install/install-visual-studio.md#step-6---install-language-packs-optional)
