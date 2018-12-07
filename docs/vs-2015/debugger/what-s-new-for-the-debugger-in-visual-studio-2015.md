---
title: Co nowego w debugerze programu Visual Studio 2015 | Dokumentacja firmy Microsoft
titleSuffix: ''
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
- debugger, what's new
- what's new [debugger]
- debugging [Visual Studio], what's new
- what's new [Visual Studio], debugging
ms.assetid: 2aed9caa-2384-4e49-8595-82d8b06cf271
caps.latest.revision: 86
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 261b3f42cb5c1040567ef16c62d3c44c5d60e0b3
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53065389"
---
# <a name="whats-new-for-the-debugger-in-visual-studio-2015"></a>Co nowego w debugerze programu Visual Studio 2015
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby uzyskać informacji o tym, co nowego w programie Visual Studio 2015 Update 1, debugowanie i Diagnostyka, zobacz [Visual Studio 2015 Update 1 informacje o wersji](https://www.visualstudio.com/news/vs2015-update1-vs#debug).

 Aby uzyskać informacji o tym, co nowego w Visual Studio 2015 RTM debugowania i diagnostyki, zobacz [Visual Studio 2015 informacje o wersji](https://www.visualstudio.com/news/vs2015-vs#debug).

## <a name="visual-studio-2015-update-1-changes"></a>Zmiany w Visual Studio 2015 Update 1
 C++, Edytuj i Kontynuuj obsługuje więcej funkcji. Aby uzyskać więcej informacji, zobacz [Edytuj i Kontynuuj (Visual C++)](../debugger/edit-and-continue-visual-cpp.md).

 Debugowanie naruszenia zasad dostępu w Visual C++, nowe okno dialogowe wyjątku określa wskaźnik, który spowodował wyjątek. Aby uzyskać więcej informacji, zobacz [w jaki sposób można debugować naruszenia zasad dostępu?](../debugger/how-can-i-debug-an-access-violation-q.md) i [usprawnienie debugowania C++ naruszenia zasad dostępu w Visual Studio 2015 Update 1](http://blogs.msdn.com/b/visualstudioalm/archive/2015/10/29/improvement-to-debugging-c-access-violations-in-visual-studio-2015-update-1.aspx)

## <a name="visual-studio-2015-rtm-debugger-ui-and-hotkey-changes"></a>Visual Studio 2015 RTM debugera interfejsu użytkownika i zmiany klawiszy skrótu
 Istnieją istotne zmiany interfejsu użytkownika w zakresie wyjątków i punkty przerwania w interfejsie użytkownika.

### <a name="breakpoints"></a>Punkty przerwania
 W programie Visual Studio 2015 to nowy sposób konfigurowania punktów przerwania, który jest **ustawienia punktu przerwania** okna.

 Poniżej przedstawiono podsumowanie okna głównego punktów przerwania i klawisze dostępu:

|Funkcja|Lokalizacja menu|Klawisz skrótu|
|-------------|-------------------|------------|
|Nowy punkt przerwania, Przełącz punkt przerwania|**Debugowanie / przełączanie punktu przerwania**<br /><br /> menu kontekstowego w edytorze / **Wstaw punkt przerwania**<br /><br /> Kliknij na lewym marginesie.|F9|
|Nowy punkt przerwania funkcji|**Debugowanie / nowy punkt przerwania / funkcji punktu przerwania**|W programie Visual Studio 2015 RTM (z żadnych aktualizacji) Użyj ALT + F9, B<br /><br /> W programie Visual Studio 2015 Update 1 lub nowszy używaj klawiszy CTRL + B|
|**Punkty przerwania** okna|**Debugowanie / Windows / punktów przerwania**|CTRL + ALT + B|
|**Ustawienia punktu przerwania**, **warunków**|menu kontekstowe dla punktu przerwania / **warunków**|ALT + F9, C|
|**Ustawienia punktu przerwania**, **akcji**|menu kontekstowe dla punktu przerwania / **akcji**|Nie skrótu|

 Aby uzyskać więcej informacji zobacz następujące artykuły:

1.  [Używanie punktów przerwania](../debugger/using-breakpoints.md)

2.  [Nowe środowisko konfiguracji punktów przerwania](http://blogs.msdn.com/b/visualstudioalm/archive/2014/10/06/new-breakpoint-configuration-experience.aspx)

3.  [Środowisko konfiguracji punktów przerwania](http://channel9.msdn.com/Events/Visual-Studio/Connect-event-2014/711)

### <a name="exception-settings"></a>Ustawienia wyjątków
 Nowy **ustawienia wyjątków** okno pozwala określić rodzaj obsługi wyjątków dla pojedynczego wyjątki lub kategorie wyjątków.

|Funkcja|Lokalizacja menu|Klawisz skrótu|
|-------------|-------------------|------------|
|**Ustawienia wyjątków** okna|**Debugowanie / Windows / Ustawienia wyjątków**|CTRL + ALT + E|

 Aby uzyskać więcej informacji zobacz następujące artykuły:

1.  [Zarządzanie wyjątkami za pomocą debugera](../debugger/managing-exceptions-with-the-debugger.md)

2.  [Nowe okno wyjątków](http://blogs.msdn.com/b/visualstudioalm/archive/2015/02/23/the-new-exception-settings-window-in-visual-studio-2015.aspx)

### <a name="edit-and-continue"></a>Edytuj i kontynuuj
 W programie Visual Studio 2015 można ustawić Edytuj i Kontynuuj w **narzędzia / Opcje / Debugowanie / ogólne** strony. W poprzednich wersjach te ustawienia zostały w kategorii oddzielne opcje.

### <a name="attach-to-process"></a>Dołącz do procesu
 W programie Visual Studio 2015 Dołącz do procesu polecenie jest dostępne tylko z menu Debugowanie. W poprzedniej wersji były dostępne z poziomu menu Narzędzia. CTRL + ALT + P klawisz skrótu działa we wszystkich wersjach.

## <a name="see-also"></a>Zobacz też
 [Debugowanie w programie Visual Studio](../debugger/debugging-in-visual-studio.md)
