---
title: Ustawienia międzynarodowe w oknie dialogowym Opcje
description: Informacje na temat używania strony ustawień międzynarodowych w sekcji środowisko w celu zmiany języka domyślnego, gdy jest zainstalowana więcej niż jedna wersja językowa środowiska IDE.
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d9dc19c69bf99ba6f66648f396468ff36444eb3f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99852274"
---
# <a name="options-dialog-box-environment--international-settings"></a>Opcje — okno dialogowe: \> międzynarodowe ustawienia środowiska

Strona Ustawienia międzynarodowe umożliwia zmianę języka domyślnego w przypadku, gdy na komputerze jest zainstalowana więcej niż jedna wersja językowa zintegrowanego środowiska programistycznego (IDE). Możesz uzyskać dostęp do tego okna dialogowego, wybierając **Opcje** z menu **Narzędzia** , a następnie wybierając **Ustawienia międzynarodowe** z folderu **środowiska** .

**Język**

Wyświetla listę języków dostępnych dla zainstalowanych wersji językowych produktu. Jeśli wiele języków produktów lub instalacja języka mieszanego współużytkuje środowisko, wybór języka zostanie zmieniony na **taki sam, jak system Microsoft Windows**.

> [!CAUTION]
> W systemie, w którym zainstalowano wiele języków, to ustawienie nie ma wpływ na narzędzia do kompilacji Visual C++ (cl.exe, link.exe, nmake.exe, bscmake.exe i powiązane pliki). Narzędzia te korzystają z wersji dla ostatniego zainstalowanego języka. Narzędzia kompilacji dla zainstalowanego wcześniej języka są zastępowane, ponieważ narzędzia do kompilowania Visual C++ nie używają satelitarnego modelu DLL.

### <a name="see-also"></a>Zobacz też

- [Instalowanie pakietów językowych](../../install/install-visual-studio.md#step-6---install-language-packs-optional)
