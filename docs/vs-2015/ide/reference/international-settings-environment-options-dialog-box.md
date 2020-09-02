---
title: Ustawienia międzynarodowe, środowisko, Opcje — okno dialogowe | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Environment.InternationalSettings
- VS.ToolsOptionsPages.Environment.International_Settings
- VS.Environment.International Settings
- VS.ToolsOptionsPag.Environment.International_Settings
helpviewer_keywords:
- International Settings dialog box
- languages, environment settings
- Options dialog box, international settings
- languages, specifying default
ms.assetid: e3a8815c-6995-4099-8e88-34f91fad55b2
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 26ed1ef8941db17c9cc087a80afcad2b4ce982de
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72650832"
---
# <a name="international-settings-environment-options-dialog-box"></a>Ustawienia międzynarodowe, środowisko, opcje — Okno dialogowe
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Strona Ustawienia międzynarodowe umożliwia zmianę języka domyślnego w przypadku, gdy na komputerze jest zainstalowana więcej niż jedna wersja językowa zintegrowanego środowiska programistycznego (IDE). Możesz uzyskać dostęp do tego okna dialogowego, wybierając **Opcje** z menu **Narzędzia** , a następnie wybierając **Ustawienia międzynarodowe** z folderu **środowiska** . Jeśli ta strona nie jest wyświetlana na liście, wybierz pozycję **Pokaż wszystkie ustawienia** w oknie dialogowym **Opcje** .

> [!NOTE]
> Opcje dostępne w oknach dialogowych oraz nazwy i lokalizacje poleceń menu, które są widoczne, mogą się różnić od tego, co opisano w pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Importuj i Eksportuj ustawienia** w menu **Narzędzia** . Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień deweloperskich w programie Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

 **Język** Wyświetla listę języków dostępnych dla zainstalowanych wersji językowych produktu. Ta opcja jest niedostępna, jeśli na maszynie nie zainstalowano więcej niż jednej wersji językowej. Jeśli wiele języków produktów lub instalacja języka mieszanego współużytkuje środowisko, wybór języka zostanie zmieniony na **taki sam, jak system Microsoft Windows**.

> [!CAUTION]
> W systemie, w którym zainstalowano wiele języków, to ustawienie nie ma wpływ na narzędzia do kompilacji Visual C++ (cl.exe, link.exe, nmake.exe, bscmake.exe i powiązane pliki). Narzędzia te używają wersji dla ostatniego zainstalowanego języka, a narzędzia dla zainstalowanego wcześniej języka są zastępowane, ponieważ narzędzia do kompilowania Visual C++ nie korzystają z modelu satelitarnej biblioteki DLL.

## <a name="see-also"></a>Zobacz też
 [Środowisko, Opcje — okno dialogowe](../../ide/reference/environment-options-dialog-box.md)
