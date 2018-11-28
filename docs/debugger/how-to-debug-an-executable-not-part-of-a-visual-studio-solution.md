---
title: 'Porady: debugowanie aplikacji, która nie jest częścią rozwiązania programu Visual Studio | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/19/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugging [Visual Studio], executables
- executable files, importing
- executable files, debugging outside of projects
ms.assetid: 3ea176e8-1ce5-42c4-b7a2-abe3a2765033
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 993af0d15245ef6391f2c9c4eb0e755e24920fe3
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/27/2018
ms.locfileid: "52388585"
---
# <a name="debug-an-app-that-isnt-part-of-a-visual-studio-solution-c-c-visual-basic-f"></a>Debuguj aplikację, która nie jest częścią rozwiązania programu Visual Studio (C++, C#, Visual Basic F#)

Chcesz debugować aplikację (*.exe* pliku), która nie jest częścią rozwiązania programu Visual Studio. Ty lub inna osoba mogła zostać utworzona aplikacja poza programem Visual Studio lub masz aplikację w innym miejscu. 

Jest zwykły sposób, aby debugować aplikację, która nie istnieje w programie Visual Studio, aby uruchomić aplikację poza programem Visual Studio, a następnie dołącz do niego przy użyciu **dołączyć do procesu** w debugerze programu Visual Studio. Aby uzyskać więcej informacji, zobacz [dołączanie do uruchomionego procesu](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
Dołączanie do aplikacji wymaga ręczne wykonanie czynności, które po kilku sekundach. Ze względu na to opóźnienie dołączanie nie pomoże, debugować problem uruchamiania lub aplikację, która nie czeka na użytkownika, danych wejściowych i szybko się kończy. 

W takich przypadkach można utworzyć projekt EXE usługi Visual Studio dla aplikacji lub zaimportować go do istniejącego C#, Visual Basic lub C++ rozwiązania. Nie wszystkie języki programowania wspierają projekty EXE. 

>[!IMPORTANT]
>Funkcje debugowania dla aplikacji, która nie została utworzona w programie Visual Studio są ograniczone, czy dołączyć do aplikacji, albo dodaj go do rozwiązania programu Visual Studio. 
>
>Jeśli masz kod źródłowy, najlepszym rozwiązaniem jest importowanie kodu do projektu programu Visual Studio. Następnie uruchom kompilację debugowania aplikacji.
>
>Jeśli nie masz kod źródłowy i aplikacja nie musi [informacje o debugowaniu](../debugger/how-to-set-debug-and-release-configurations.md) w zgodnym formacie, dostępne funkcje debugowania są bardzo mało. 

### <a name="to-create-a-new-exe-project-for-an-existing-app"></a>Aby utworzyć nowy projekt EXE dla istniejącej aplikacji  
   
1. W programie Visual Studio, wybierz **pliku** > **Otwórz** > **projektu**.  
   
1. W **Otwórz projekt** okno dialogowe, wybierz opcję **wszystkie pliki projektu**, jeśli jeszcze nie wybrano, w menu rozwijanym obok **nazwy pliku**.  
   
1. Przejdź do *.exe* plików, wybierz ją, a następnie wybierz **Otwórz**.  
   
   Plik pojawi się w rozwiązaniu programu Visual Studio do nowego, tymczasowego.

1. Rozpocznij debugowanie aplikacji, wybierając polecenie wykonania, takie jak **Rozpocznij debugowanie**, z **debugowania** menu.    
  
### <a name="to-import-an-app-into-an-existing-visual-studio-solution"></a>Aby zaimportować aplikację do istniejącego rozwiązania Visual Studio  
  
1.  Przy użyciu języka C++ C#, lub wybierz rozwiązanie programu Visual Basic Otwórz w programie Visual Studio, **pliku** > **Dodaj** > **istniejący projekt**.  
  
1. W **Otwórz projekt** okno dialogowe, wybierz opcję **wszystkie pliki projektu**, jeśli jeszcze nie wybrano, w menu rozwijanym obok **nazwy pliku**.  
   
1. Przejdź do *.exe* plików, wybierz ją, a następnie wybierz **Otwórz**.  
   
   Plik pojawi się jako nowy projekt w bieżącym rozwiązaniu.  
   
1. Za pomocą nowego pliku wybrane, rozpocząć debugowanie aplikacji, wybierając polecenie wykonania, takie jak **Rozpocznij debugowanie**, z **debugowania** menu.    
  
### <a name="see-also"></a>Zobacz także  
 [Ustawienia debugera i przygotowanie](../debugger/debugger-settings-and-preparation.md)   
 [Zabezpieczenia debugera](../debugger/debugger-security.md)   
 [DBG, pliki](/previous-versions/visualstudio/visual-studio-2010/da528y14(v=vs.100))