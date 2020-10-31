---
title: Ustawienia międzynarodowe w oknie dialogowym Opcje
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 1210f217c9e1dc1f8a90eb99fec9e55970aa8eff
ms.sourcegitcommit: f1bb1b66ed141837e992b3352ce68ff24c11f53e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2020
ms.locfileid: "93102496"
---
# <a name="options-dialog-box-environment--international-settings"></a>Opcje — okno dialogowe: \> międzynarodowe ustawienia środowiska

Strona Ustawienia międzynarodowe umożliwia zmianę języka domyślnego w przypadku, gdy na komputerze jest zainstalowana więcej niż jedna wersja językowa zintegrowanego środowiska programistycznego (IDE). Możesz uzyskać dostęp do tego okna dialogowego, wybierając **Opcje** z menu **Narzędzia** , a następnie wybierając **Ustawienia międzynarodowe** z folderu **środowiska** .

**Język**

Wyświetla listę języków dostępnych dla zainstalowanych wersji językowych produktu. Jeśli wiele języków produktów lub instalacja języka mieszanego współużytkuje środowisko, wybór języka zostanie zmieniony na **taki sam, jak system Microsoft Windows** .

> [!CAUTION]
> W systemie, w którym zainstalowano wiele języków, to ustawienie nie ma wpływ na narzędzia do kompilacji Visual C++ (cl.exe, link.exe, nmake.exe, bscmake.exe i powiązane pliki). Narzędzia te korzystają z wersji dla ostatniego zainstalowanego języka. Narzędzia kompilacji dla zainstalowanego wcześniej języka są zastępowane, ponieważ narzędzia do kompilowania Visual C++ nie używają satelitarnego modelu DLL.

### <a name="see-also"></a>Zobacz też

- [Instalowanie pakietów językowych](../../install/install-visual-studio.md#step-6---install-language-packs-optional)
