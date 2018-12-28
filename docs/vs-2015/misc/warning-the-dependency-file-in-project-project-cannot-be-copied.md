---
title: 'Ostrzeżenie: zależność &#39;pliku&#39; w projekcie &#39;projektu&#39; nie można skopiować do katalogu uruchomienia, ponieważ zastąpiłaby ona odwołanie &#39;pliku. &#39; | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.tasklisterror.copy_version_warning
ms.assetid: 116819f3-a4d4-48b5-9e71-7c54660d38ef
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 3b24a14636726be15aa52a50d56c381781f492fc
ms.sourcegitcommit: 159ed9d4f56cdc1dff2fd19d9dffafe77e46cd4e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2018
ms.locfileid: "53739584"
---
# <a name="warning-the-dependency-39file39-in-project-39project39-cannot-be-copied-to-the-run-directory-because-it-would-overwrite-the-reference-39file39"></a>Ostrzeżenie: zależność &#39;pliku&#39; w projekcie &#39;projektu&#39; nie można skopiować do katalogu uruchomienia, ponieważ zastąpiłaby ona odwołanie &#39;pliku.&#39;
Istnieje konflikt między zależności więcej niż jeden plik distinct zestawu o takiej samej nazwie, zostaną skopiowane do katalogu bin do uruchomienia aplikacji. Katalogu uruchamiania jest w stanie rozwiązać konfliktu, ponieważ jednej z zależności jest odwołanie podstawowe.  
  
 Dwukrotne kliknięcie ten element listy zadań spowoduje przejście do węzła podstawowego odwołania, który powoduje konflikt.  
  
 To ostrzeżenie występuje, gdy występuje konflikt zależności, ale korzystano wokół niego, dodając jeden z powodujących konflikty zależności jako odwołanie. Lub może mieć ma odwołania w wersji 1, a następnie dodać drugiego odwołania które odwołuje się do wersji 2 w pierwszym odwołaniu.  
  
 Oznacza to, że ten błąd występuje, ponieważ projekty w rozwiązaniu istnieją odwołania do siebie nawzajem, ale odwołania zostały utworzone jako odwołania do pliku (przy użyciu **Przeglądaj** znajdujący się w [Dodaj odwołanie](http://msdn.microsoft.com/en-us/2feb0fe2-0805-4cc9-8cba-b0315849dfb7) okna dialogowego pole), zamiast odwołania projektu do projektu (przy użyciu **projektu** karcie **Dodaj odwołanie** okno dialogowe). Zaletą odwołania projektu do projektu jest to, że tworzy ono zależność między projektami w systemie kompilacji, tak aby projekt zależny zostanie skompilowany, jeśli została zmieniona od czasu ostatniego konstruowania projektu z odwołaniem. Odwołanie pliku nie tworzy zależność kompilacji, więc istnieje możliwość skompilowania projektu z odwołaniem bez kompilowania projektu zależnego, więc odwołanie może się okazać zbędne; Projekt może odwoływać się do uprzednio utworzonej wersji projektu. Może to spowodować, że kilka wersjach pojedynczego pliku DLL jest wymagany w katalogu bin, nie jest możliwe, która powoduje ten komunikat o błędzie.  
  
 Ten komunikat pojawia się za każdym razem, gdy występuje konflikt w katalogu bin i aplikacji może nie działać prawidłowo. Mimo że może korzystano tego problemu, to ostrzeżenie nadal będą wyświetlane, system projektu nie może ustalić, czy wersja zależności będą działać poprawnie, ze wszystkimi składnikami.  
  
 **Aby naprawić ten błąd**  
  
-   Do katalogu bin, co można zrobić poprzez umieszczenie plików zestawu do globalnej pamięci podręcznej, należy skopiować pliki zestawu jednej (lub zero). Global assembly cache rozwiązuje konflikty nazw plików. Ponieważ środowisko uruchomieniowe języka wspólnego wie, jak znaleźć zestawy w globalnej pamięci podręcznej, zostaną wprowadzone nie lokalne kopie pliku zestawu. Aby uzyskać więcej informacji, zobacz [Praca z zestawami i Global Assembly Cache](http://msdn.microsoft.com/library/8a18e5c2-d41d-49ef-abcb-7c27e2469433) i [błąd: nie można skopiować zależności 'Plik' w projekcie 'projekt' do katalogu uruchomienia, ponieważ spowodowałoby to konflikt z zależnością ' Plik "](/visualstudio/misc/error-dependency-file?view=vs-2015).  
  
## <a name="see-also"></a>Zobacz też  
 [Zarządzanie odwołaniami w projekcie](../ide/managing-references-in-a-project.md)   
 [Globalna pamięć podręczna zestawów](http://msdn.microsoft.com/library/cf5eacd0-d3ec-4879-b6da-5fd5e4372202)   
 [Instrukcje: Tworzenie i usuwanie zależności projektu](../ide/how-to-create-and-remove-project-dependencies.md)