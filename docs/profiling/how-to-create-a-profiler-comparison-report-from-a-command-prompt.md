---
title: Tworzenie raportu porównawczego profilera (wiersz polecenia)
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 00548d16-eb5b-46f7-8a65-862f98a43831
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: d370a7465428da4f2582f4f765c1d81ae017af48
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809391"
---
# <a name="how-to-create-a-profiler-comparison-report-from-a-command-prompt"></a>Instrukcje: Tworzenie raportu porównania profilera z wiersza polecenia
Można wygenerować [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] raport narzędzia profilowania, który porównuje dane wydajności dwóch danych profilowania (.* /or VSP* . *vsps*) plikach. Raport przedstawia różnice, regresje wydajności i ulepszenia, które wystąpiły w jednej sesji profilowania. Wartości w raporcie przedstawiają różnice lub zmieniają się od linii bazowej pierwszego określonego pliku. Ta różnica jest obliczana przez określenie różnicy między starą wartością, czyli wartością bazową, a wartością wyniku z nowej analizy. Porównania danych profilera mogą opierać się na funkcjach w kodzie, modułach w aplikacji, wierszach, wskaźnikach instrukcji (IP) i typach.

 Aby wyświetlić listę identyfikatorów kategorii i pól porównania, wpisz w wierszu polecenia następujący tekst:

 **VSPerfReport/querydifftables**  *VspFileName1* *VspFileName2*

 Aby utworzyć raport porównawczy, należy użyć następującej składni:

 **VSPerfReport/diff** `VspFileName1` *VspFileName2* [ **/** `Options` ]  

 Opcje z poniższej tabeli można dodać do wiersza polecenia **VSPerfReport/diff** .

|Opcja|Opis|
|------------|-----------------|
|**DiffThreshold:**[*wartość*]|Zignoruj różnicę, jeśli jest niższa od tej wartości progu procentowego. Ponadto nie będą wyświetlane nowe dane zawierające wartości poniżej tego progu.|
|**Diffie:** *tabelaname*|Ta tabela służy do porównywania plików. Domyślnie tabela Functions jest używana. Określ identyfikator, który jest wymieniony w **VSPerfReport/querydifftables**.|
|**DiffColumn:** *ColumnName*|Ta kolumna służy do porównywania wartości. Domyślnie jest używana kolumna procent wyłącznych próbek. Określ identyfikator, który jest wymieniony w **VSPerfReport/querydifftables**.|
