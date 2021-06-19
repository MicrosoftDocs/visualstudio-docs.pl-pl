---
title: Proces transformacji szablonu tekstowego
description: Dowiedz się, że proces przekształcania szablonu tekstu przyjmuje plik szablonu tekstowego jako dane wejściowe i generuje nowy plik tekstowy jako dane wyjściowe.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, transformation process
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8dc827039253c21effffcc82d70b4f66ff284738
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388597"
---
# <a name="the-text-template-transformation-process"></a>Proces transformacji szablonu tekstowego
Proces przekształcania szablonu tekstu przyjmuje plik szablonu tekstowego jako dane wejściowe i generuje nowy plik tekstowy jako dane wyjściowe. Na przykład możesz użyć szablonów tekstowych do wygenerowania kodu Visual Basic lub C# albo wygenerować raport HTML.

 W tym procesie biorą udział trzy składniki: aparat, host i procesory dyrektywy. Aparat kontroluje proces; Współdziała z hostem i procesorem dyrektywy w celu uzyskania pliku wyjściowego. Host zapewnia wszelkie interakcje ze środowiskiem, takie jak lokalizowanie plików i zestawów. Procesor dyrektywy dodaje funkcje, takie jak odczytywanie danych z pliku XML lub bazy danych.

 Proces przekształcania szablonu tekstu jest wykonywany w dwóch krokach. Najpierw aparat tworzy tymczasową klasę, która jest znana jako wygenerowana klasa przekształcenia. Ta klasa zawiera kod generowany przez dyrektywy i bloki sterujące. Następnie aparat kompiluje i wykonuje wygenerowaną klasę przekształcania w celu wygenerowania pliku wyjściowego.

## <a name="components"></a>Składniki

|Składnik|Opis|Dostosowywalne (tak/nie)|
|-|-|-|
|Aparat|Składnik aparatu kontroluje proces przekształcania szablonu tekstu|Nie.|
|Host|Host jest interfejsem między aparatem a środowiskiem użytkownika. Visual Studio jest hostem procesu przekształcania tekstu.|Tak. Możesz napisać niestandardowego hosta.|
|Procesory dyrektyw|Procesory dyrektyw to klasy, które obsługują dyrektywy w szablonach tekstowych. Za pomocą dyrektyw można dostarczać dane do szablonu tekstowego ze źródła danych wejściowych.|Tak. Można pisać niestandardowe procesory dyrektyw|

## <a name="the-engine"></a>Aparat
 Aparat odbiera szablon jako ciąg z hosta, który obsługuje wszystkie pliki używane w procesie przekształcania. Następnie aparat prosi hosta o zlokalizowanie niestandardowych procesorów dyrektyw i innych aspektów środowiska. Aparat następnie kompiluje i uruchamia wygenerowaną klasę przekształcania. Aparat zwraca wygenerowany tekst do hosta, który zwykle zapisuje tekst w pliku.

## <a name="the-host"></a>Host
 Host jest odpowiedzialny za wszystkie elementy, które odnoszą się do środowiska poza procesem przekształcania, w tym za następujące elementy:

- Lokalizowanie plików tekstowych i binarnych żądanych przez aparat lub procesor dyrektywy. Host może wyszukiwać katalogi i globalną pamięć podręczną zestawów w celu zlokalizowania zestawów. Host może zlokalizować niestandardowy kod procesora dyrektywy dla aparatu. Host może również lokalizować i odczytywać pliki tekstowe oraz zwracać ich zawartość jako ciągi.

- Dostarczanie list standardowych zestawów i przestrzeni nazw, które są używane przez aparat do tworzenia wygenerowanej klasy przekształcania.

- Podanie domeny aplikacji używanej podczas kompilowania i wykonywania wygenerowanej klasy przekształcania przez aparat. Do ochrony aplikacji hosta przed błędami w kodzie szablonu jest używana oddzielna domena aplikacji.

- Zapisywanie wygenerowanego pliku wyjściowego.

- Ustawienie domyślnego rozszerzenia dla wygenerowanego pliku wyjściowego.

- Obsługa błędów przekształcania szablonu tekstu. Na przykład host może wyświetlać błędy w interfejsie użytkownika lub zapisywać je w pliku. (W Visual Studio błędy są wyświetlane w oknie komunikatu o błędzie).

- Podanie wymaganej wartości parametru, jeśli użytkownik wywoła dyrektywę bez dostarczania wartości. Procesor dyrektywy może określić nazwę dyrektywy i parametr i poprosić hosta o podanie wartości domyślnej, jeśli ją ma.

## <a name="directives-and-directive-processors"></a>Dyrektywy i procesory dyrektyw
 Dyrektywa to polecenie w szablonie tekstowym. Udostępnia parametry procesu generowania. Zazwyczaj dyrektywy definiują źródło i typ modelu lub inne dane wejściowe oraz rozszerzenie nazwy pliku wyjściowego.

 Procesor dyrektywy może przetwarzać co najmniej jedną dyrektywę. Podczas przekształcania szablonu musisz mieć zainstalowany procesor dyrektywy, który może poradzić sobie z dyrektywami w szablonie.

 Dyrektywy działają przez dodanie kodu w wygenerowanej klasie przekształcania. Wywołujesz dyrektywy z szablonu tekstowego, a aparat przetwarza wszystkie wywołania dyrektywy podczas tworzenia wygenerowanej klasy przekształcania. Po pomyślnym wywołaniu dyrektywy pozostała część kodu zapisywana w szablonie tekstowym może polegać na funkcjach zapewnianych przez dyrektywę. Na przykład możesz wykonać następujące wywołanie dyrektywy `import` w szablonie:

 `<#@ import namespace="System.Text" #>`

 Procesor dyrektywy standardowej konwertuje to na `using` instrukcje w wygenerowanej klasie przekształcania. Następnie możesz użyć `StringBuilder` klasy w pozostałej części kodu szablonu bez kwalifikowania jej jako `System.Text.StringBuilder` .
