---
title: 'Wprowadzenie z PTVS: Rozpocznij kodowanie (projekty) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-python
ms.topic: conceptual
ms.assetid: 14b85e70-b9a8-415c-a307-8c8c316a0495
caps.latest.revision: 7
author: kraigb
ms.author: kraigb
manager: jillfra
ms.openlocfilehash: 28622f290d82f86bf3d18cc4f40cfcfc8e953dad
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62537156"
---
# <a name="getting-started-with-ptvs-start-coding-projects"></a>Pierwsze kroki z narzędziami PTVS: rozpoczęcie kodowania (projekty)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Python Tools for Visual Studio (PTVS) ułatwia zarządzanie kodem. 
 
 Możesz obejrzeć te instrukcje w bardzo krótkim [filmie wideo](https://www.youtube.com/watch?v=KHPoVpL7zHg&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=2)w serwisie YouTube. 
 
 Jeśli wcześniej korzystano z języka Python, wiadomo, że projekt jest zdefiniowany przez sposób układania plików na dysku. Jest to doskonałe rozwiązanie w przypadku zwykłych projektów Python, ale jeśli masz więcej plików (strony sieci Web z JavaScript, testy jednostkowe i skrypty kompilacji), systemy plików mogą zaczynać się ograniczać. Program Visual Studio używa projektów do osiągnięcia trzech rzeczy. 
 
- Zidentyfikuj pliki krytyczne. Ważne pliki są tymi, które są sprawdzane w systemie kontroli wersji (pliki źródłowe, zasoby itp.), ale nie pliki generowane jako dane wyjściowe kompilacji. Ważne pliki są również tymi, które można skopiować na inny komputer, aby ktoś inny mógł go obejść w Twojej aplikacji. 
 
- Określ, w jaki sposób mają być używane pliki. Pliki, które muszą być przetwarzane przez narzędzie zawsze, gdy pliki zostaną zmienione. Projekty programu Visual Studio mogą przechwytywać te informacje 
 
- Zdefiniuj granice składników. Jeśli masz wiele składników w aplikacji, możesz umieścić każdą z nich w osobnym projekcie. Mogą one zostać wdrożone na różnych serwerach utworzonych przy użyciu różnych ustawień kompilacji lub debugowania lub nawet mogą być zapisywane przy użyciu innego języka obsługiwanego przez program Visual Studio, np. C++ lub Node.js 
 
  Istnieje kilka szablonów projektów, które ułatwiają rozpoczęcie pracy. Jeśli masz już kod w języku Python, nad którym chcesz korzystać, Kreator z istniejącego kodu pomoże Ci utworzyć projekt, który zawiera wszystkie pliki. Dla niektórych popularnych platform istnieją różne projekty sieci Web. Więcej szablonów jest dostępnych w pakiecie przykładów PTVS. Dostępne są opcje, które umożliwiają współpracują z innymi strukturami. Szablon aplikacji języka Python to czysty, pusty projekt. Istnieje jeden moduł, aby rozpocząć pracę. 
 
  Program Visual Studio Wyświetla otwarte projekty w oknie Eksplorator rozwiązań, w tym wszystkie pliki, ścieżki wyszukiwania i środowiska języka Python. Aby dodać nowe elementy, wybierz folder projektu, a następnie z menu kontekstowego (naciśnij przycisk prawy wskaźnik), wybierz Dodaj, a następnie nowy element. Możesz wybrać dowolny element w oknie dialogowym, dostosować nazwę elementu i dodać element do projektu. 
 
  Możesz przeciągać i upuszczać do Eksplorator rozwiązań. Jeśli pliki zostały już skopiowane do struktury katalogów projektu, możesz wybrać opcję Pokaż wszystkie pliki w górnej części Eksplorator rozwiązań. Następnie możesz wybrać elementy, które chcesz dodać, a następnie z menu kontekstowego wybrać opcję Dołącz do projektu. 
 
  Możesz obejrzeć te instrukcje w bardzo krótkim [filmie wideo](https://www.youtube.com/watch?v=KHPoVpL7zHg&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=2)w serwisie YouTube. 
 
## <a name="see-also"></a>Zobacz też 
 [Dokumentacja typu wiki](https://github.com/Microsoft/PTVS/wiki/Projects) [PTVS wprowadzenie i głębokie wideo szczegółowe](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)
