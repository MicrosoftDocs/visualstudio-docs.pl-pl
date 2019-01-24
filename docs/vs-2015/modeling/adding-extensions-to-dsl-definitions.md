---
title: Dodawanie rozszerzeń do definicji DSL | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 07e133be-92ab-4936-a02b-45d2012bd0a6
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: bd45a2345e6e5b28b74cb27fac226514c3f92a04
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54766277"
---
# <a name="adding-extensions-to-dsl-definitions"></a>Dodawanie rozszerzeń do definicji DSL
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Rozszerzenie definicji DSL umożliwia tworzenie pakietu rozszerzenia języka specyficznego dla domeny (DSL). Rozszerzenia DSL, który jest zawarty w Visual Studio Integration rozszerzenie (VSIX), można zainstalować na komputerze użytkownika w taki sam sposób jak element DSL. Dodatkowe funkcje można dynamicznie włączone i wyłączone w czasie wykonywania. Językami DSL nie muszą być jawnie zaprojektowane dla rozszerzenia, a rozszerzenia można zaprojektować później lub stron trzecich bez zmiany rozszerzonej DSL.  
  
 Dodatkowe funkcje mogą być następujące:  
  
- Właściwości elementów modelu i prezentacji  
  
- Dekoratory dla kształtów i łączników  
  
- Klasy, relacje, kształty i łączniki  
  
- Ograniczenia sprawdzania poprawności  
  
- Karty i elementów przybornika  
  
  Użytkownik rozszerzonej DSL można utworzyć i zapisać modelu, który zawiera wystąpienia dodatkowych funkcji i może zostać odczytany przez innych użytkowników, którzy mają zainstalowane odpowiednie rozszerzenie. Użytkownicy, którzy nie zainstalowano rozszerzenia nie można użyć dodatkowych funkcji, ale można zaktualizować i zapisywanie modelu bez utraty dodatkowe funkcje.  
  
  Przykładowy kod i więcej informacji na temat tej funkcji można znaleźć [Visual Studio Visualization i Modeling SDK](http://go.microsoft.com/fwlink/?LinkID=186128) witryny sieci Web.  
  
## <a name="see-also"></a>Zobacz też  
 [Visual Studio Visualisation i Modeling SDK](http://go.microsoft.com/fwlink/?LinkID=186128)
