---
title: Proces przekształcania szablonu tekstu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, transformation process
ms.assetid: 80b3f0e0-49e7-4865-a1ac-dba068abe96b
caps.latest.revision: 32
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7322724b2118cb8b844262696a6e7cbd91a74e9b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72658503"
---
# <a name="the-text-template-transformation-process"></a>Proces transformacji szablonu tekstowego
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Proces przekształcania szablonu tekstu pobiera plik szablonu tekstu jako dane wejściowe i generuje nowy plik tekstowy jako dane wyjściowe. Na przykład można użyć szablonów tekstowych do generowania kodu Visual Basic lub C# lub można wygenerować raport HTML.

 Trzy składniki biorą udział w tym procesie: silnik, Host i procesory dyrektywy. Aparat kontroluje proces; współdziała z hostem i procesorem dyrektywy w celu utworzenia pliku wyjściowego. Host zapewnia wszelkie interakcje ze środowiskiem, takie jak Lokalizowanie plików i zestawów. Procesor dyrektywy dodaje funkcje, takie jak odczytywanie danych z pliku XML lub bazy danych.

 Proces przekształcania szablonu tekstu jest wykonywany w dwóch krokach. Najpierw aparat tworzy klasę tymczasową, która jest znana jako wygenerowana Klasa transformacji. Ta klasa zawiera kod generowany przez dyrektywy i bloki sterujące. Następnie aparat kompiluje i wykonuje wygenerowaną klasę transformacji w celu utworzenia pliku wyjściowego.

## <a name="components"></a>Składniki

|Składnik|Opis|Dostosowywalne (tak/nie)|
|---------------|-----------------|------------------------------|
|Aparat|Składnik silnika kontroluje proces transformacji szablonu tekstu|Nie.|
|Host|Host jest interfejsem między aparatem i środowiskiem użytkownika. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] jest hostem procesu transformacji tekstu.|Tak. Można napisać hosta niestandardowego.|
|Procesory dyrektywy|Procesory dyrektywy to klasy, które obsługują dyrektywy w szablonach tekstowych. Możesz użyć dyrektyw, aby dostarczyć dane do szablonu tekstu ze źródła danych wejściowych.|Tak. Możesz pisać niestandardowe procesory dyrektywy|

## <a name="the-engine"></a>Aparat
 Aparat odbiera szablon jako ciąg z hosta, który obsługuje wszystkie pliki, które są używane w procesie transformacji. Następnie silnik prosi hosta o znalezienie wszelkich niestandardowych procesorów dyrektywy i innych aspektów środowiska. Następnie aparat kompiluje i uruchamia wygenerowaną klasę transformacji. Aparat zwraca wygenerowany tekst do hosta, który zwykle zapisuje tekst do pliku.

## <a name="the-host"></a>Host
 Host jest odpowiedzialny za wszystkie elementy, które odnoszą się do środowiska poza procesem transformacji, w tym następujące:

- Lokalizowanie plików tekstowych i binarnych żądanych przez aparat lub procesor dyrektywy. Host może przeszukiwać katalogi i globalną pamięć podręczną zestawów w celu lokalizowania zestawów. Host może zlokalizować niestandardowy kod procesora dyrektywy dla aparatu. Host może również lokalizować i odczytywać pliki tekstowe i zwracać ich zawartość jako ciągi.

- Dostarczanie list standardowych zestawów i przestrzeni nazw, które są używane przez aparat do tworzenia wygenerowanej klasy transformacji.

- Udostępnianie domeny aplikacji, która jest używana, gdy aparat kompiluje i wykonuje wygenerowaną klasę transformacji. Oddzielna domena aplikacji jest używana w celu ochrony aplikacji hosta przed błędami w kodzie szablonu.

- Zapisywanie wygenerowanego pliku wyjściowego.

- Ustawianie domyślnego rozszerzenia dla wygenerowanego pliku wyjściowego.

- Obsługa błędów transformacji szablonu tekstu. Na przykład host może wyświetlać Błędy w interfejsie użytkownika lub zapisywać je do pliku. (W programie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Błędy są wyświetlane w oknie komunikatu o błędzie).

- Podanie wymaganej wartości parametru, jeśli użytkownik wywołał dyrektywę bez podawania wartości. Procesor dyrektywy może określić nazwę dyrektywy i parametr i poprosił hosta o podanie wartości domyślnej, jeśli ma.

## <a name="directives-and-directive-processors"></a>Dyrektywy i procesory dyrektywy
 Dyrektywa to polecenie w szablonie tekstu. Zawiera parametry procesu generacji. Dyrektywy zazwyczaj definiują źródło i typ modelu lub inne dane wejściowe oraz rozszerzenie nazwy pliku wyjściowego.

 Procesor dyrektywy może przetworzyć jedną lub więcej dyrektyw. Podczas przekształcania szablonu należy zainstalować procesor dyrektywy, który może zajmować się dyrektywami w szablonie.

 Dyrektywy działają przez dodanie kodu do wygenerowanej klasy transformacji. Należy wywołać dyrektywy z szablonu tekstowego, a aparat przetwarza wszystkie wywołania dyrektywy podczas tworzenia wygenerowanej klasy transformacji. Po pomyślnym wywołaniu dyrektywy pozostała część kodu, którą można napisać w szablonie tekstu, może opierać się na funkcjach dostępnych w dyrektywie. Na przykład w szablonie można wykonać następujące wywołanie do `import` dyrektywy:

 `<#@ import namespace="System.Text" #>`

 Procesor dyrektywy standardowej konwertuje ten element na `using` instrukcję w wygenerowanej klasie transformacji. Następnie można użyć `StringBuilder` klasy w pozostałej części kodu szablonu bez kwalifikowania go jako `System.Text.StringBuilder` .
