---
title: '&#39;Ostrzeżenie: plik&#39; zależności w &#39;projekcie&#39; projektu nie może zostać skopiowany do katalogu uruchomieniowego, ponieważ spowodowałoby to zastąpienie pliku &#39;referencyjnego. &#39; | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
f1_keywords:
- vs.tasklisterror.copy_version_warning
ms.assetid: 116819f3-a4d4-48b5-9e71-7c54660d38ef
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a619168bd07fde5d27e5c3d87dc46f505cf5268d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672818"
---
# <a name="warning-the-dependency-39file39-in-project-39project39-cannot-be-copied-to-the-run-directory-because-it-would-overwrite-the-reference-39file39"></a>&#39;Ostrzeżenie: plik&#39; zależności w &#39;projekcie&#39; projektu nie może zostać skopiowany do katalogu uruchomieniowego, ponieważ spowodowałoby to zastąpienie pliku &#39;referencyjnego.&#39;
Występuje konflikt między zależnościami. więcej niż jeden plik zestawu DISTINCT o tej samej nazwie powinien zostać skopiowany do katalogu bin, aby można było uruchomić aplikację. Katalog uruchamiania może rozwiązać konflikt, ponieważ jedna z zależności jest odwołaniem podstawowym.

 Dwukrotne kliknięcie tego elementu Lista zadań spowoduje przejście do podstawowego węzła odwołania powodującego konflikt.

 To ostrzeżenie występuje w przypadku konfliktu zależności, ale pracowało nad nim przez dodanie jednej z zależności powodujących konflikt jako odwołania. Może istnieć odwołanie do wersji 1, a następnie dodano drugie odwołanie, które sama odwołuje się do wersji 2 pierwszego odwołania.

 Oznacza to, że ten błąd występuje, ponieważ projekty w rozwiązaniu zawierają odwołania do siebie, ale odwołania zostały utworzone jako odwołania do pliku (za pomocą przycisku **Przeglądaj** w oknie dialogowym [Dodaj odwołanie](https://msdn.microsoft.com/2feb0fe2-0805-4cc9-8cba-b0315849dfb7) ), a nie projektu do projektu odwołania (za pomocą karty **projekt** w oknie dialogowym **Dodaj odwołanie** ). Zaletą projektu w odniesieniu do projektu jest utworzenie zależności między projektami w systemie kompilacji, dzięki czemu projekt zależny zostanie skompilowany, jeśli został zmieniony od czasu skompilowania projektu odniesienia. Odwołanie do pliku nie tworzy zależności kompilacji, więc możliwe jest skompilowanie odwołującego się projektu bez kompilowania projektu zależnego, więc odwołanie może stać się przestarzałe. projekt może odwoływać się do wcześniej skompilowanej wersji projektu. Może to spowodować, że w katalogu bin jest wymagana kilka wersji pojedynczej biblioteki DLL, co nie jest możliwe i spowoduje to przeprowadzenie tego komunikatu o błędzie.

 Ten komunikat jest wyświetlany za każdym razem, gdy w katalogu bin występuje konflikt, a aplikacja może nie funkcjonować prawidłowo. Mimo że ten problem mógł obejść, to ostrzeżenie będzie nadal wyświetlane, ponieważ system projektu nie może określić, czy wersja zależności będzie działała poprawnie ze wszystkimi składnikami.

 **Aby poprawić ten błąd**

- Skopiuj jeden (lub zero) plik zestawu do katalogu bin, który można wykonać, umieszczając pliki zestawu w globalnej pamięci podręcznej zestawów. Globalna pamięć podręczna zestawów rozwiązuje konflikty nazw plików. Nie zostanie wykonana żadna lokalna kopia pliku zestawu, ponieważ środowisko uruchomieniowe języka wspólnego wie, jak znaleźć zestawy w globalnej pamięci podręcznej zestawów. Aby uzyskać więcej informacji, zobacz [Praca z zestawami i globalną pamięcią podręczną zestawów](https://msdn.microsoft.com/library/8a18e5c2-d41d-49ef-abcb-7c27e2469433) i [błąd: nie można skopiować zależności "plik" w projekcie "Project" do katalogu uruchomieniowego, ponieważ spowodowałoby to konflikt z zależnością "plik"](/visualstudio/misc/error-dependency-file?view=vs-2015).

## <a name="see-also"></a>Zobacz też
 [Zarządzanie odwołaniami w](../ide/managing-references-in-a-project.md) [globalnej pamięci podręcznej zestawów](https://msdn.microsoft.com/library/cf5eacd0-d3ec-4879-b6da-5fd5e4372202) projektu [instrukcje: Tworzenie i usuwanie zależności projektu](../ide/how-to-create-and-remove-project-dependencies.md)