---
title: Zalecane ustawienia właściwości debugera dla C#, VB | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], managed
- debugging managed code, recommended property settings
ms.assetid: 3d14a8d4-2925-44d0-be41-ec546d411db9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 07c63a70de9d633ccd73d1d0d3bd23196d421543
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72731371"
---
# <a name="managed-debugging-recommended-property-settings"></a>Zarządzanie debugowaniem: zalecane ustawienia właściwości
Niektóre właściwości powinny być ustawiane w taki sam sposób dla wszystkich zarządzanych scenariuszy debugowania.

 W poniższych tabelach są wyświetlane zalecane ustawienia właściwości.

 Ustawienia niewymienione w tym miejscu mogą się różnić między różnymi typami projektów zarządzanych. Na przykład **Akcja uruchamiania** zostanie ustawiona inaczej w projekcie Windows Forms niż w projekcie [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].

### <a name="configuration-properties-on-the-build-c-or-compile-visual-basic-tab"></a>Właściwości konfiguracji na karcie kompilacja (C#) lub kompilacja (Visual Basic)

|**Nazwa właściwości**|**Konfigurowania**|
|-----------------------|-----------------|
|**Zdefiniuj stałą DEBUG**|C#i F#: Ustaw pole wyboru na zaznaczone. Dzięki temu aplikacja może używać klasy Debug.|
|**Zdefiniuj stałą TRACE**|C#i F#: Ustaw pole wyboru na zaznaczone. Dzięki temu aplikacja może używać klasy śledzenia.|
|**Optymalizuj kod**|C#, F#i Visual Basic: Ustaw wartość false. Zoptymalizowany kod jest trudniejszy do debugowania, ponieważ wygenerowane instrukcje nie odpowiadają bezpośrednio na kod źródłowy. Jeśli okaże się, że program ma usterkę, która pojawia się tylko w zoptymalizowanym kodzie, można włączyć to ustawienie, ale pamiętaj, że kod wyświetlany w oknie **demontażu** jest generowany na podstawie zoptymalizowanego źródła, które może nie odpowiadać temu, co widzisz w edytorze kodu. Aby debugować zoptymalizowany kod, należy wyłączyć Tylko mój kod. (Zobacz [ograniczanie do tylko mój kod](../debugger/navigating-through-code-with-the-debugger.md#BKMK_Restrict_stepping_to_Just_My_Code)).<br /><br /> Aby uzyskać więcej informacji, zobacz [Ustawienia projektu C# dla konfiguracji debugowania](../debugger/project-settings-for-csharp-debug-configurations.md) lub [ustawienia projektu dla konfiguracji debugowania Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md).|
|**Ścieżka wyjściowa**|Ustaw na bin\Debug \\.|
|**Zaawansowane opcje kompilacji**|Tylko Visual Basic. Kliknij przycisk **Zaawansowane** , aby ustawić zaawansowane właściwości, które są opisane w poniższej tabeli.|

### <a name="advanced-compiler-settings-dialog-box"></a>Zaawansowane ustawienia kompilatora — Okno dialogowe

|**Nazwa właściwości**|**Konfigurowania**|
|-----------------------|-----------------|
|**Włącz optymalizacje**|Ustaw wartość false dla powodów określonych w opcji **Optymalizuj kod** w powyższej tabeli.|
|**Generuj informacje o debugowaniu**|Zaznacz to pole wyboru, aby spowodować, że flaga/DEBUG ma być ustawiana podczas kompilacji, co spowoduje wygenerowanie informacji niezbędnych do ułatwienia debugowania.|
|**Zdefiniuj stałą DEBUG**|Zaznacz to pole wyboru, aby zdefiniować stałą `DEBUG`, która umożliwia aplikacji korzystanie z klasy <xref:System.Diagnostics.Debug>.|
|**Zdefiniuj stałą TRACE**|Zaznacz to pole wyboru, aby zdefiniować stałą `TRACE`, która umożliwia aplikacji korzystanie z klasy <xref:System.Diagnostics.Trace>.|

## <a name="see-also"></a>Zobacz także
- [Debugowanie kodu zarządzanego](../debugger/debugging-managed-code.md)
- [Typy projektów C#, F# i Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)