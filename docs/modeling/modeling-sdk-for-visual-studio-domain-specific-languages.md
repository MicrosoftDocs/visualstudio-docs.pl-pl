---
title: Modelowanie SDK dla Visual Studio — języki specyficzne dla domeny
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools
- Domain-Specific Language
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2abb209943ff14969f71ebdca6982020f30a5d47
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590205"
---
# <a name="modeling-sdk-for-visual-studio---domain-specific-languages"></a>Modelowanie SDK dla Visual Studio — języki specyficzne dla domeny

Za pomocą zestawu Modeling SDK for Visual Studio, można utworzyć zaawansowane opartych na modelu narzędzia programistyczne, które można zintegrować z programem Visual Studio. W ten sam sposób można utworzyć co najmniej jedną definicję modelu i zintegrować ją w zestaw narzędzi.

Centralnym elementem zestawu MSDK jest definicja modelu tworzona w celu przedstawienia koncepcji z obszaru biznesowego. Można otoczyć model z szeroką gamą narzędzi, takich jak widok diagramowy, możliwość generowania kodu i innych artefaktów, polecenia przekształcania modelu oraz możliwość interakcji z kodem i innych obiektów w programie Visual Studio. Podczas opracowywania modelu można połączyć go z innymi modelami i narzędziami w celu utworzenia zestawu narzędzi o dużych możliwościach, który będzie wspomagał proces projektowania.

Zestaw MSDK umożliwia szybkie opracowanie modelu z użyciem języka specyficznego dla domeny (DSL). Należy rozpocząć od użycia specjalnego edytora w celu zdefiniowania schematu lub abstrakcyjnej składni wraz z notacją graficzną. Na podstawie tej definicji zestaw VMSDK generuje następujące elementy:

- Implementacja modelu z silnie typizowanym interfejsem API, który działa w magazynie opartym na transakcjach.

- Eksplorator oparty na drzewie.

- Edytor graficzny, w którym użytkownicy mogą wyświetlać zdefiniowany model lub jego części.

- Metody serializacji zapisujące modele w przystosowanych do odczytu plikach XML.

- Możliwości generowania kodu programu i innych artefaktów przy użyciu funkcji tworzenia szablonów tekstu.

Wszystkie te funkcje można dostosowywać i rozszerzać. Rozszerzenia są integrowane w taki sposób, że można aktualizować definicję DSL oraz ponownie generować funkcje bez utraty używanych rozszerzeń.

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

[Wpisy w blogu pokrewne](https://devblogs.microsoft.com/devops/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/)
