---
title: Dodawanie rozszerzeń do definicji DSL | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 07e133be-92ab-4936-a02b-45d2012bd0a6
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: aeeac82b27b4b5bb71ed05ba658bf9ee048bd85d
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74292149"
---
# <a name="adding-extensions-to-dsl-definitions"></a>Dodawanie rozszerzeń do definicji DSL
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Rozszerzenie definicji DSL umożliwia utworzenie pakietu rozszerzeń dla języka specyficznego dla domeny (DSL). Rozszerzenie DSL, które jest zawarte w rozszerzeniu integracji programu Visual Studio (VSIX), można zainstalować na komputerze użytkownika w taki sam sposób, jak w przypadku połączenia DSL. Dodatkowe funkcje mogą być dynamicznie włączane i wyłączane w czasie wykonywania. Językami DSL nie muszą być jawnie przeznaczone do rozszerzenia, a rozszerzenia mogą być zaprojektowane później lub przez inne firmy bez zmiany rozszerzonego połączenia DSL.

 Dostępne są następujące dodatkowe funkcje:

- Właściwości elementów model i prezentacja

- Dekoratory dla kształtów i łączników

- Klasy, relacje, kształty i łączniki

- Ograniczenia walidacji

- Elementy i karty przybornika

  Użytkownik o rozszerzonej linii DSL może utworzyć i zapisać model, który zawiera wystąpienia dodatkowych funkcji, i może zostać odczytany przez innych użytkowników, którzy zainstalowali odpowiednie rozszerzenie. Użytkownicy, którzy nie zainstalowali rozszerzenia, nie mogą korzystać z dodatkowych funkcji, ale mogą aktualizować i zapisywać model bez utraty dodatkowych funkcji.

  Aby zapoznać się z przykładowym kodem i więcej informacji na temat tej funkcji, zobacz witrynę sieci Web [Visual Studio Wizualizacja i Modeling SDK](https://go.microsoft.com/fwlink/?LinkID=186128) .

## <a name="see-also"></a>Zobacz też
 [Visual Studio Wizualizacja i Modeling SDK](https://go.microsoft.com/fwlink/?LinkID=186128)
