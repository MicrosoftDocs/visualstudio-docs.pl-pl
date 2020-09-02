---
title: 'Instrukcje: Tworzenie raportu porównania profilera z wiersza polecenia | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 00548d16-eb5b-46f7-8a65-862f98a43831
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8c6dabbae5f2d3758aebe0562f99767ee6993d80
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68179570"
---
# <a name="how-to-create-a-profiler-comparison-report-from-a-command-prompt"></a>Porady: tworzenie raportu porównania profilera z wiersza polecenia
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można wygenerować [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] raport narzędzia profilowania, który porównuje dane wydajności dwóch danych profilowania (. /Or VSP. VSPS). Raport przedstawia różnice, regresje wydajności i ulepszenia, które wystąpiły w jednej sesji profilowania. Wartości w raporcie przedstawiają różnice lub zmieniają się od linii bazowej pierwszego określonego pliku. Ta różnica jest obliczana przez określenie różnicy między starą wartością, czyli wartością bazową, a wartością wyniku z nowej analizy. Porównania danych profilera mogą opierać się na funkcjach w kodzie, modułach w aplikacji, wierszach, wskaźnikach instrukcji (IP) i typach.  
  
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
