---
title: 'Debugowanie zarządzane: Zalecane ustawienia właściwości | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], managed
- debugging managed code, recommended property settings
ms.assetid: 3d14a8d4-2925-44d0-be41-ec546d411db9
caps.latest.revision: 32
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6c82a624e5a2847da5c0f85a9e2ef4180a338a34
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51724699"
---
# <a name="managed-debugging-recommended-property-settings"></a>Zarządzanie debugowaniem: zalecane ustawienia właściwości
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Taki sam sposób dla wszystkich zarządzanych scenariuszy debugowania można ustawić niektórych właściwości.  
  
 Poniższe tabele zawierają zalecane ustawienia właściwości.  
  
 Ustawienia niewymienione w tym miejscu mogą się różnić między różnymi typami projektów zarządzanych. Na przykład **Akcja uruchamiania** zostanie ustawione inaczej w projekcie programu Windows Forms niż w [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] projektu.  
  
### <a name="configuration-properties-on-the-build-c-or-compile-visual-basic-tab"></a>Właściwości konfiguracji na karcie kompilacja (C#) lub Kompiluj (Visual Basic)  
  
|**Nazwa właściwości**|**Ustawienie**|  
|-----------------------|-----------------|  
|**Zdefiniuj stałą DEBUG**|C#i F#: Ustaw pole wyboru zaznaczone. Dzięki temu aplikacja korzysta z klasy Debug.|  
|**Zdefiniuj stałą TRACE**|C#i F#: Ustaw pole wyboru zaznaczone. Dzięki temu aplikacja korzysta z klasy Trace.|  
|**Optymalizuj kod**|C#, F#i Visual Basic: Ustaw na wartość false. Zoptymalizowany kod jest trudniejszy do debugowania, ponieważ wygenerowane instrukcje nie odpowiadają bezpośrednio kodowi źródłowemu. Jeśli okaże się, że program ma błąd, który pojawia się tylko w zoptymalizowanym kodzie, można włączyć to ustawienie, ale należy pamiętać, że kod w **dezasemblacji** okna jest generowany na podstawie zoptymalizowane źródła, które mogą być niezgodne zobaczyć w kodzie Edytor. Aby debugować zoptymalizowany kod, należy wyłączyć funkcję [tylko mój kod](just-my-code.md).<br /><br /> Aby uzyskać więcej informacji, zobacz [ustawienia projektu dla języka C# Debuguj konfiguracje](../debugger/project-settings-for-csharp-debug-configurations.md) lub [ustawienia projektu dla konfiguracji debugowania języka Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md).|  
|**Ścieżka wyjściowa**|Ustaw bin\Debug\\.|  
|**Zaawansowane opcje kompilacji**|Tylko Visual Basic. Kliknij przycisk **zaawansowane** Aby ustawić zaawansowane właściwości, które są opisane w poniższej tabeli.|  
  
### <a name="advanced-compiler-settings-dialog-box"></a>Zaawansowane ustawienia kompilatora — Okno dialogowe  
  
|**Nazwa właściwości**|**Ustawienie**|  
|-----------------------|-----------------|  
|**Włącz optymalizacje**|Ustaw wartość false dla przyczyn wymienionych w **Optymalizuj kod** opcji w powyższej tabeli.|  
|**Generuj informacje debugowania**|Zaznacz to pole wyboru, aby spowodować, że można ustawić podczas kompilowania kodu, flagi/Debug, która spowoduje wygenerowanie informacji potrzebnych do ułatwienia debugowania.|  
|**Zdefiniuj stałą DEBUG**|Zaznacz to pole wyboru, aby zdefiniować `DEBUG` stałą, która pozwala aplikacji używać <xref:System.Diagnostics.Debug> klasy.|  
|**Zdefiniuj stałą TRACE**|Zaznacz to pole wyboru, aby zdefiniować `TRACE` stałą, która pozwala aplikacji używać <xref:System.Diagnostics.Trace> klasy.|  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie zarządzanego kodu](../debugger/debugging-managed-code.md)   
 [Typy projektów C#, F# i Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)



