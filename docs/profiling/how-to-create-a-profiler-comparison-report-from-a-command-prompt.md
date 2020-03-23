---
title: 'Jak: Tworzenie raportu porównania profilera z wiersza polecenia | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 00548d16-eb5b-46f7-8a65-862f98a43831
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: d0328e04067770f8837d10d532abb67d16c65e50
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74776430"
---
# <a name="how-to-create-a-profiler-comparison-report-from-a-command-prompt"></a>Jak: Tworzenie raportu porównania profilera z wiersza polecenia
Można wygenerować raport Narzędzia [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] profilowania, który porównuje dane dotyczące wydajności dwóch danych profilowania (.* vsp* /lub . *vsps*) Pliki. Raport pokazuje różnice, regresji wydajności i ulepszenia, które wystąpiły z jednej sesji profilowania do drugiej. Wartości w raporcie przedstawiają delta lub zmiany od linii bazowej pierwszego pliku, który określisz. Ta delta jest obliczana przez określenie różnicy między starą wartością, która jest wartością bazową, a wartością wyniku z nowej analizy. Porównania danych profilera mogą być oparte na funkcjach w kodzie, modułach w aplikacji, wierszach, wskaźnikach instrukcji (IP) i typach.

 Aby wyświetlić listę identyfikatorów kategorii i pól porównania, wpisz następujący wiersz polecenia:

 **VSPerfReport /querydifftables**  *VspFileName1* *VspFileNameme2*

 Aby utworzyć raport porównawczy, użyj następującej składni:

 **VSPerfReport /diff** `VspFileName1` *VspFileName2* [**/**`Options`]  

 Opcje z poniższej tabeli można dodać do wiersza polecenia **VSPerfReport /diff.**

|Opcja|Opis|
|------------|-----------------|
|**DiffThreshold:**[*Wartość*]|Nie uwzględnij różnicy, jeśli jest poniżej tej wartości progu procentowego. Ponadto nowe dane z wartościami, które są poniżej tego progu nie pojawią się.|
|**Tabela różnicowa:** *Nazwa tabeli*|Ta tabela służy do porównywania plików. Domyślnie używana jest tabela funkcji. Określ identyfikator, który jest wymieniony w **VSPerfReport /querydifftables**.|
|**DiffColumn:** *Nazwa kolumny*|Ta kolumna służy do porównywania wartości. Domyślnie używana jest kolumna procentu wyłącznych próbek. Określ identyfikator, który jest wymieniony w **VSPerfReport /querydifftables**.|
