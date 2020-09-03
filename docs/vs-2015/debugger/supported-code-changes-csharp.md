---
title: Obsługiwane zmiany kodu (C#) | Microsoft Docs
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
ms.openlocfilehash: 6fc02c11a4ebceea431fc06a1bd1cfdb1063097d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "67823536"
---
# <a name="supported-code-changes-c"></a>Obsługiwane zmiany kodu (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Edytuj i Kontynuuj obsługuje większość typów zmian kodu w treści metody. Większość zmian poza treściami metod oraz kilka zmian w obrębie treści metody nie można zastosować podczas debugowania. Aby zastosować te nieobsługiwane zmiany, należy zatrzymać debugowanie i ponownie uruchomić za pomocą nowej wersji kodu.  
  
 Następujące zmiany nie mogą zostać zastosowane do kodu w języku C# podczas sesji debugowania:  
  
- Zmiany bieżącej instrukcji lub dowolnej innej aktywnej instrukcji.  
  
     Aktywne instrukcje obejmują wszystkie instrukcje w funkcjach w stosie wywołań, które zostały wywołane w celu uzyskania bieżącej instrukcji.  
  
     Bieżąca instrukcja jest oznaczona za pomocą żółtego tła w oknie źródło. Inne aktywne instrukcje są oznaczone cieniowanym tłem i są tylko do odczytu. Te domyślne kolory można zmienić w oknie dialogowym **Opcje** .  
  
- Zmiana sygnatury typu.  
  
- Dodawanie anonimowej metody, która przechwytuje zmienną, która nie została wcześniej przechwycona.  
  
- Dodawanie, usuwanie lub zmiana atrybutów.  
  
- Dodawanie, usuwanie lub zmiana `using` dyrektyw.  
  
- Dodawanie `foreach` , `using` , lub `lock` dookoła aktywnej instrukcji.  
  
## <a name="unsafe-code"></a>Kod niebezpieczny  
 Zmiany w niebezpiecznym kodzie mają takie same ograniczenia jak zmiany w bezpiecznym kodzie, z jednym dodatkowym ograniczeniem: polecenie Edytuj i Kontynuuj nie obsługuje zmian w niebezpiecznym kodzie, który opuszcza metodę, która zawiera `stackalloc` operator.  
  
## <a name="exceptions"></a>Wyjątki  
 Polecenie Edytuj i Kontynuuj obsługuje zmiany `catch` w `finally` blokach i, z tą różnicą, że dodanie `catch` `finally` bloku or wokół aktywnej instrukcji jest niedozwolone.  
  
## <a name="unsupported-scenarios"></a>Nieobsługiwane scenariusze  
 Edytuj i Kontynuuj nie są dostępne w następujących scenariuszach debugowania:  
  
- Debugowanie kodu LINQ w pewnych okolicznościach. Aby uzyskać więcej informacji, zobacz [debugowanie LINQ](../debugger/debugging-linq.md).  
  
  - Przechwytywanie zmiennej, która nie została wcześniej przechwycona.  

  - Zmiana typu wyrażenia zapytania (np., wybierz a => wybrać nowy {A = a};)  

  - Usuwanie elementu zawierającego `where` aktywną instrukcję.  

  - Usuwanie elementu zawierającego `let` aktywną instrukcję.  

  - Usuwanie elementu zawierającego `join` aktywną instrukcję.  

  - Usuwanie elementu zawierającego `orderby` aktywną instrukcję.  
  
- Debugowanie w trybie mieszanym (natywnym/zarządzanym).  
  
- Debugowanie SQL.  
  
- Debugowanie zrzutu Dr. Watson.  
  
- Edytowanie kodu po nieobsługiwanym wyjątku, gdy opcja "**odwinięcie stosu wywołań w przypadku nieobsługiwanych wyjątków**" nie jest zaznaczona.  
  
- Debugowanie osadzonej aplikacji środowiska uruchomieniowego.  
  
- Debugowanie aplikacji, która została **dołączona do** programu zamiast uruchamiania aplikacji, wybierając pozycję **Rozpocznij** z menu **Debuguj** .  
  
- Debugowanie zoptymalizowanego kodu.  
  
- Debugowanie starej wersji kodu od momentu kompilacji nowej wersji nie powiodło się z powodu błędów kompilacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Edytuj i Kontynuuj (Visual C#)](../debugger/edit-and-continue-visual-csharp.md)   
 [Instrukcje: używanie funkcji Edytuj i kontynuuj (C#)](../debugger/how-to-use-edit-and-continue-csharp.md)
