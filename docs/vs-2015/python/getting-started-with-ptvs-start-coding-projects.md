---
title: 'Wprowadzenie do narzędzi PTVS: Rozpoczęcie kodowania (projekty) | Dokumentacja firmy Microsoft'
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
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54781072"
---
# <a name="getting-started-with-ptvs-start-coding-projects"></a>Wprowadzenie do narzędzi PTVS: Rozpoczęcie kodowania (projekty)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Narzędzia Python Tools for Visual Studio (PTVS) pomaga w zarządzaniu kodu. 
 
 Możesz obserwować te instrukcje w bardzo krótkim [wideo usługi youtube](https://www.youtube.com/watch?v=KHPoVpL7zHg&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=2). 
 
 Jeśli używano Python przed wiesz, że Twój projekt został zdefiniowany przez sposób układania pliki na dysku. To rozwiązanie idealne dla zwykłych projektów języka Python, ale jeśli masz więcej plików (strony sieci web przy użyciu języka JavaScript, testy jednostkowe i skrypty kompilacji), systemów plików można uruchomić za chwilę ograniczającą. Visual Studio używa projekty do osiągnięcia trzy rzeczy. 
 
- Zidentyfikuj krytyczne pliki. Ważne pliki są tymi, które możesz sprawdzić w systemie kontroli wersji (pliki źródłowe, zasoby itd.), ale nie pliki, które są generowane jako dane wyjściowe kompilacji. Ważne pliki są również te, które może spowodować skopiowanie na inny komputer, ktoś inny może pracować w aplikacji. 
 
- Określ, jak pliki powinna być używana. Może być pliki, które to narzędzie musi przetworzyć po każdym wprowadzeniu zmiany plików. Projektów programu Visual Studio można przechwytywać te informacje 
 
- Zdefiniuj granice składników. Jeśli masz wiele składników w aplikacji, można umieścić ją w osobnym projekcie. Te po pewnym czasie można wdrażać na różnych serwerach, skompilowanych przy użyciu różnych kompilacji lub ustawienia debugowania lub nawet mogłyby być zapisywane przy użyciu innego języka, obsługiwane przez program Visual Studio, takich jak C++ i Node.js 
 
  Istnieje kilka szablonów projektów, które pomogą Ci rozpocząć pracę. Jeśli masz już kodu w języku Python, który chcesz pracować, kreatora z istniejącego kodu pomoże Ci utworzyć projekt, który zawiera wszystkie pliki. Istnieje wiele projektów sieci Web dla niektórych popularnych platform. Więcej szablonów są dostępne w pakiecie przykłady PTVS. Dostępne są opcje umożliwiają podanej sieci web, szablony działać z innych platform. Szablon aplikacji w języku Python jest jasny, pusty projekt. Istnieje jeden moduł ułatwią Ci rozpoczęcie pracy. 
 
  Visual Studio Wyświetla otwartych projektów w oknie Eksploratora rozwiązań, w tym wszystkie pliki, ścieżki wyszukiwania i środowiska Python. Aby dodać nowe elementy, wybierz folder projektu, a następnie z menu kontekstowego (naciśnij przycisk prawo wskaźnika) wybierz pozycję Dodaj, a następnie nowy element. Można wybrać dowolny element w oknie dialogowym, dostosować nazwy elementu i Dodaj element do projektu. 
 
  Można przeciągnąć i upuścić w Eksploratorze rozwiązań. Jeśli została już pliki zostały skopiowane do struktury katalogu projektu, można wybierać Pokaż wszystkie pliki w górnej części Eksploratora rozwiązań. Można następnie wybierz elementy, które chcesz dodać, a z menu kontekstowego wybierz Include w projekcie. 
 
  Możesz obserwować te instrukcje w bardzo krótkim [wideo usługi youtube](https://www.youtube.com/watch?v=KHPoVpL7zHg&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=2). 
 
## <a name="see-also"></a>Zobacz też 
 [Dokumentacja witryny typu wiki](https://github.com/Microsoft/PTVS/wiki/Projects) [PTVS rozpoczynania pracy i Deep Dive filmów wideo](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)
