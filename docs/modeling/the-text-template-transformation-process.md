---
title: Proces przekształcania szablonu tekstowego
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, transformation process
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 29495fb297670b6b297e17d40bfb2bcdc0025862
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55929326"
---
# <a name="the-text-template-transformation-process"></a>Proces przekształcania szablonu tekstowego
Proces przekształcania szablonu tekstowego przyjmuje plik szablonu tekstu jako dane wejściowe i generuje nowy plik tekstowy jako dane wyjściowe. Na przykład można użyć szablonów tekstowych do generowania kodu Visual Basic lub C# lub możesz wygenerować raport HTML.

 Trzy składniki wzięcia udziału w ramach tego procesu: silnik, hosta i procesorów dyrektyw. Aparat kontroluje proces; współpracuje z usługą hosta oraz procesor dyrektywy, aby wygenerować plik wyjściowy. Host zawiera wszystkie interakcje ze środowiskiem, takich jak lokalizowanie plików i zestawów. Procesor dyrektywy dodaje funkcje, takie jak odczytywanie danych z pliku XML lub bazy danych.

 Proces przekształcania szablonu tekstowego odbywa się w dwóch krokach. Po pierwsze aparat tworzy tymczasowej klasy, który jest znany jako wygenerowanej klasy przekształcenia. Ta klasa zawiera kod, który jest generowany przez dyrektywy i bloków sterujących. Po tym aparat kompiluje i wykonuje wygenerowanej klasy przekształcenia do tworzenia pliku wyjściowego.

## <a name="components"></a>Składniki

|Składnik|Opis|Można dostosować (tak/nie)|
|-|-|-|
|Aparat|Składnik aparatu kontroluje proces przekształcania szablonu tekstowego|Nie.|
|Host|Host jest interfejs między aparatem programu i środowisko użytkownika. Program Visual Studio jest hostem proces przekształcania tekstu.|Tak. Możesz napisać niestandardowego hosta.|
|Procesory dyrektywy|Procesory dyrektywy są klasach, które obsługują dyrektywy w szablonach tekstowych. Dyrektywy służy do przekazywania danych do szablonu tekstu ze źródła danych wejściowych.|Tak. Możesz napisać niestandardowego procesory dyrektywy|

## <a name="the-engine"></a>Aparat
 Aparat odbiera szablon jako ciąg znaków z hosta, która obsługuje wszystkie pliki, które są używane w procesie transformacji. Aparat są następnie prosi hosta, aby zlokalizować wszystkie niestandardowe procesory dyrektyw i innych aspektów środowiska. Aparat następnie kompiluje i uruchamia wygenerowanej klasy przekształcenia. Aparat powraca wygenerowanego tekstu do hosta, który normalnie zapisuje tekst w pliku.

## <a name="the-host"></a>Host
 Host jest odpowiedzialny za nic, które odnoszą się do środowiska poza procesem przekształcania, takie jak następujące:

-   Wyszukiwanie tekstowe i pliki binarne, żądane przez aparat lub procesor dyrektywy. Host może przeszukiwać katalogi i globalnej pamięci podręcznej do lokalizowania zestawów. Hosta można zlokalizować kod niestandardowy procesor dyrektywy dla aparatu. Hosta można zlokalizować i odczytywać pliki tekstowe i zwróć ich zawartość jako ciągi.

-   Dostarczanie listy standardowe zestawy i przestrzenie nazw, które są używane przez aparat do tworzenia wygenerowanej klasy przekształcenia.

-   Zapewnianie domenie aplikacji, która jest używana, gdy aparat zostanie skompilowany i wykonany wygenerowanej klasy przekształcenia. Oddzielna domena aplikacji jest używana w celu ochrony aplikacji hosta z błędów w kodzie szablonu.

-   Zapisywanie pliku wygenerowanych danych wyjściowych.

-   Ustawienie domyślne rozszerzenie pliku wygenerowanych danych wyjściowych.

-   Obsługa błędów przekształcania szablonu tekstu. Na przykład host może wyświetlić błędy w interfejsie użytkownika lub zostaną zapisane do pliku. (W programie Visual Studio, błędy są wyświetlane w oknie komunikat o błędzie.)

-   Podanie wartości wymaganego parametru, jeśli użytkownik wywołał dyrektywy bez podawania wartości. Procesor dyrektywy można określić nazwy dyrektywy i parametru i poproś hosta, aby podać wartość domyślną, jeśli taki istnieje.

## <a name="directives-and-directive-processors"></a>Dyrektywy i procesorów dyrektyw
 Dyrektywy to polecenie w szablonie tekstowym. Zawiera parametry procesu tworzenia. Zwykle dyrektywy określają źródło i typu modelu i inne dane wejściowe i rozszerzenie nazwy pliku wyjściowego pliku.

 Procesor dyrektywy może przetwarzać jeden lub więcej dyrektywy. Kiedy przekształcasz szablon, musisz zainstalować procesor dyrektywy, którego poradzenie sobie z dyrektywy w szablonie.

 Dyrektywy działają przez dodanie kodu w wygenerowanej klasy przekształcenia. Możesz wywołać dyrektyw szablonu tekstu i procesy aparatu dyrektywy wywołania, podczas tworzenia wygenerowanej klasy przekształcenia. Po wywołaniu metody dyrektywy pomyślnie, reszta kodu napisanego w szablonie tekstowym może polegać na funkcjonalności, jaką zapewnia dyrektywa. Na przykład, można wykonać następujące wywołanie do `import` dyrektywy w szablonie:

 `<#@ import namespace="System.Text" #>`

 Standardowa procesor dyrektywy konwertuje ten element, aby `using` instrukcji w wygenerowanej klasy przekształcenia. Następnie można użyć `StringBuilder` klasy w pozostałej części kodu szablonu bez kwalifikowania go jako `System.Text.StringBuilder`.