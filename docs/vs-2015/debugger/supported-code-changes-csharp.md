---
title: Obsługiwane zmiany kodu (C#) | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Edit and Continue [C#], supported code changes
ms.assetid: c7a48ea9-5a7f-4328-a9d7-f0e76fac399d
caps.latest.revision: 30
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cc1c6183eece2799d99907cd5f5ec9489a268542
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60117658"
---
# <a name="supported-code-changes-c"></a>Obsługiwane zmiany kodu (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Edytuj i Kontynuuj obsługuje większość typów zmian kodu w treści metod. Większość zmian poza treści metod i drobne zmiany w treści metod, nie można zastosować podczas debugowania, jednak. Aby zastosować te nieobsługiwane zmiany, należy zatrzymać debugowanie i ponownie uruchom za pomocą nowej wersji kodu.  
  
 Następujące zmiany nie można zastosować do kodu w języku C# w podczas sesji debugowania:  
  
- Zmiany bieżącej instrukcji lub aktywnej instrukcji.  
  
     Aktywne instrukcje obejmują dowolnej instrukcji w funkcjach w stosie wywołań, które zostały wywołane do bieżącej instrukcji.  
  
     Bieżąca instrukcja jest oznaczony za żółtym tłem w oknie źródła. Inne aktywne instrukcje są oznaczane przez cieniowanego tła i są przeznaczone tylko do odczytu. Te kolory domyślne można zmienić w programie **opcje** okno dialogowe.  
  
- Zmienianie podpisu typu.  
  
- Dodawanie metody anonimowej, które przechwytuje zmienną, która nie została przechwycona wcześniej.  
  
- Dodawanie, usuwanie lub zmiana atrybutów.  
  
- Dodawanie, usuwanie i zmienianie `using` dyrektywy.  
  
- Dodawanie `foreach`, `using`, lub `lock` aktywnej instrukcji.  
  
## <a name="unsafe-code"></a>Niebezpieczny kod  
 Zmiany w niebezpieczny kod mają te same ograniczenia co wprowadzenia zmian w kodzie bezpiecznym, za pomocą jednego dodatkowych ograniczeń: Edytuj i Kontynuuj nie obsługuje zmiany niebezpieczny kod, który istnieje w metodzie, która zawiera `stackalloc` operatora.  
  
## <a name="exceptions"></a>Wyjątki  
 Edytuj i Kontynuuj obsługuje zmiany `catch` i `finally` blokuje, z tą różnicą, że dodanie `catch` lub `finally` bloku aktywnej instrukcji jest niedozwolone.  
  
## <a name="unsupported-scenarios"></a>Nieobsługiwane scenariusze  
 Edytuj i Kontynuuj nie jest dostępna w następujących scenariuszach debugowania:  
  
- Debugowanie kodu LINQ w pewnych okolicznościach. Aby uzyskać więcej informacji, zobacz [debugowania LINQ](../debugger/debugging-linq.md).  
  
    - Przechwytuje zmienną, która nie została przechwycona wcześniej.  
  
    - Zmiana typu wyrażenia zapytania (np. Wybierz = > Wybierz nowy {A =};)  
  
    - Usuwanie `where` zawierający aktywnej instrukcji.  
  
    - Usuwanie `let` zawierający aktywnej instrukcji.  
  
    - Usuwanie `join` zawierający aktywnej instrukcji.  
  
    - Usuwanie `orderby` zawierający aktywnej instrukcji.  
  
- Debugowanie trybu mieszanego (natywnego/zarządzanego).  
  
- Debugowanie SQL.  
  
- Debugowanie odzyskiwania po awarii. Zrzut programu Watson.  
  
- Edytowanie kodu po wystąpieniu nieobsługiwanego wyjątku podczas "**Unwind na stosie wywołań dotycząca nieobsłużonych wyjątków**" opcja nie jest zaznaczona.  
  
- Debugowanie aplikacji osadzonego środowiska uruchomieniowego.  
  
- Debugowanie aplikacji, która ma **dołączyć do** zamiast uruchamiać aplikację, wybierając **Start** z **debugowania** menu.  
  
- Debugowanie zoptymalizowanego kodu.  
  
- Debugowanie starą wersję kodu po nowej wersji nie powiodło się skompilowanie z powodu błędów kompilacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Edytuj i Kontynuuj (Visual C#)](../debugger/edit-and-continue-visual-csharp.md)   
 [Instrukcje: Korzystanie z funkcji Edytuj i kontynuuj (C#)](../debugger/how-to-use-edit-and-continue-csharp.md)
