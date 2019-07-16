---
title: Proces przekształcania szablonu tekstu | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, transformation process
ms.assetid: 80b3f0e0-49e7-4865-a1ac-dba068abe96b
caps.latest.revision: 32
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 0f92b4053006aa5da3c28d9330b372466f84d0fd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68199959"
---
# <a name="the-text-template-transformation-process"></a>Proces transformacji szablonu tekstowego
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Proces przekształcania szablonu tekstowego przyjmuje plik szablonu tekstu jako dane wejściowe i generuje nowy plik tekstowy jako dane wyjściowe. Na przykład można użyć szablonów tekstowych do generowania kodu Visual Basic lub C# lub możesz wygenerować raport HTML.  
  
 Trzy składniki wzięcia udziału w ramach tego procesu: silnik, hosta i procesorów dyrektyw. Aparat kontroluje proces; współpracuje z usługą hosta oraz procesor dyrektywy, aby wygenerować plik wyjściowy. Host zawiera wszystkie interakcje ze środowiskiem, takich jak lokalizowanie plików i zestawów. Procesor dyrektywy dodaje funkcje, takie jak odczytywanie danych z pliku XML lub bazy danych.  
  
 Proces przekształcania szablonu tekstowego odbywa się w dwóch krokach. Po pierwsze aparat tworzy tymczasowej klasy, który jest znany jako wygenerowanej klasy przekształcenia. Ta klasa zawiera kod, który jest generowany przez dyrektywy i bloków sterujących. Po tym aparat kompiluje i wykonuje wygenerowanej klasy przekształcenia do tworzenia pliku wyjściowego.  
  
## <a name="components"></a>Składniki  
  
|Składnik|Opis|Można dostosować (tak/nie)|  
|---------------|-----------------|------------------------------|  
|Aparat|Składnik aparatu kontroluje proces przekształcania szablonu tekstowego|Nie.|  
|Host|Host jest interfejs między aparatem programu i środowisko użytkownika. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] to host proces przekształcania tekstu.|Tak. Możesz napisać niestandardowego hosta.|  
|Procesory dyrektywy|Procesory dyrektywy są klasach, które obsługują dyrektywy w szablonach tekstowych. Dyrektywy służy do przekazywania danych do szablonu tekstu ze źródła danych wejściowych.|Tak. Możesz napisać niestandardowego procesory dyrektywy|  
  
## <a name="the-engine"></a>Aparat  
 Aparat odbiera szablon jako ciąg znaków z hosta, która obsługuje wszystkie pliki, które są używane w procesie transformacji. Aparat są następnie prosi hosta, aby zlokalizować wszystkie niestandardowe procesory dyrektyw i innych aspektów środowiska. Aparat następnie kompiluje i uruchamia wygenerowanej klasy przekształcenia. Aparat powraca wygenerowanego tekstu do hosta, który normalnie zapisuje tekst w pliku.  
  
## <a name="the-host"></a>Host  
 Host jest odpowiedzialny za nic, które odnoszą się do środowiska poza procesem przekształcania, takie jak następujące:  
  
- Wyszukiwanie tekstowe i pliki binarne, żądane przez aparat lub procesor dyrektywy. Host może przeszukiwać katalogi i globalnej pamięci podręcznej do lokalizowania zestawów. Hosta można zlokalizować kod niestandardowy procesor dyrektywy dla aparatu. Hosta można zlokalizować i odczytywać pliki tekstowe i zwróć ich zawartość jako ciągi.  
  
- Dostarczanie listy standardowe zestawy i przestrzenie nazw, które są używane przez aparat do tworzenia wygenerowanej klasy przekształcenia.  
  
- Zapewnianie domenie aplikacji, która jest używana, gdy aparat zostanie skompilowany i wykonany wygenerowanej klasy przekształcenia. Oddzielna domena aplikacji jest używana w celu ochrony aplikacji hosta z błędów w kodzie szablonu.  
  
- Zapisywanie pliku wygenerowanych danych wyjściowych.  
  
- Ustawienie domyślne rozszerzenie pliku wygenerowanych danych wyjściowych.  
  
- Obsługa błędów przekształcania szablonu tekstu. Na przykład host może wyświetlić błędy w interfejsie użytkownika lub zostaną zapisane do pliku. (W [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], błędy są wyświetlane w oknie komunikatu błędu.)  
  
- Podanie wartości wymaganego parametru, jeśli użytkownik wywołał dyrektywy bez podawania wartości. Procesor dyrektywy można określić nazwy dyrektywy i parametru i poproś hosta, aby podać wartość domyślną, jeśli taki istnieje.  
  
## <a name="directives-and-directive-processors"></a>Dyrektywy i procesorów dyrektyw  
 Dyrektywy to polecenie w szablonie tekstowym. Zawiera parametry procesu tworzenia. Zwykle dyrektywy określają źródło i typu modelu i inne dane wejściowe i rozszerzenie nazwy pliku wyjściowego pliku.  
  
 Procesor dyrektywy może przetwarzać jeden lub więcej dyrektywy. Kiedy przekształcasz szablon, musisz zainstalować procesor dyrektywy, którego poradzenie sobie z dyrektywy w szablonie.  
  
 Dyrektywy działają przez dodanie kodu w wygenerowanej klasy przekształcenia. Możesz wywołać dyrektyw szablonu tekstu i procesy aparatu dyrektywy wywołania, podczas tworzenia wygenerowanej klasy przekształcenia. Po wywołaniu metody dyrektywy pomyślnie, reszta kodu napisanego w szablonie tekstowym może polegać na funkcjonalności, jaką zapewnia dyrektywa. Na przykład, można wykonać następujące wywołanie do `import` dyrektywy w szablonie:  
  
 `<#@ import namespace="System.Text" #>`  
  
 Standardowa procesor dyrektywy konwertuje ten element, aby `using` instrukcji w wygenerowanej klasy przekształcenia. Następnie można użyć `StringBuilder` klasy w pozostałej części kodu szablonu bez kwalifikowania go jako `System.Text.StringBuilder`.
