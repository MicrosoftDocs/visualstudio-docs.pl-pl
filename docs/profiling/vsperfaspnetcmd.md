---
title: Polecenie VSPerfASPNetCmd | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling tools,VSPerfASPNETCmd
- VSPerfASPNETCmd
ms.assetid: f9e9f895-57bb-41e8-8bd1-cdaa738ec220
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a9b175cb5dd0c555aeaaafb30b7927c3fc81bff4
ms.sourcegitcommit: c9a01c599ce19a5845605b3b28c0229fd0abb93f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2018
ms.locfileid: "52281761"
---
# <a name="vsperfaspnetcmd"></a>VSPerfASPNetCmd
**VSPerfASPNetCmd.exe** narzędzie wiersza polecenia umożliwia witryn sieci web platformy ASP.Net profilu bez konieczności ustawiania zmiennych środowiskowych, lub uruchom ponownie komputer. Użyj **VSPerfASPNetCmd.exe** zamiast [VSPerfCmd](../profiling/vsperfcmd.md) podczas profilowany witryn sieci Web platformy ASP.NET i nie są dodatkowe funkcje udostępniane przez **VSPerfCmd**. Aby uzyskać więcej informacji na temat **VSPerfASPNetCmd**, zobacz [profilowania szybkie witryn sieci web za pomocą polecenia VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md). **Polecenie VSPerfASPNetCmd** to narzędzie preferowanych wiersza polecenia do użycia podczas korzystania z Autonomiczny profiler profilowanie witryny sieci web ASP.NET.  
  
## <a name="syntax"></a>Składnia  
 **polecenie vsperfaspnetcmd** [/*opcje*] *witryny sieci Web*  
  
## <a name="options"></a>Opcje  
  
|Opcja|Opis|  
|------------|-----------------|  
|**/ Przykładowe** lub **/s**|Profile witryny sieci Web przy użyciu metody próbkowania. **/ Przykładowe** jest domyślną metodą. / Przykładowe nie można używać z **/Trace**.|  
|**/ Trace** lub   **/t**|Profile witryny sieci Web przy użyciu metody instrumentacji. / Śledzenia nie można używać z **/Sample**.|  
|**/ Pamięci**[**:**`Type`] lub **/m**[**:**{**a**&#124;**l**}]|Służą do profilowania alokacji pamięci i opcjonalnie profile czasów istnienia obiektów (wyrzucania elementów bezużytecznych). **/ Pamięci** mogą być używane z pobieranie próbek lub metody instrumentacji.<br /><br /> *Typ* może być jedną z następujących czynności:<br /><br /> -   **Alokacja** (lub **a**) zbiera tylko dane alokacji pamięci.<br />-   **okres istnienia** (lub **l**) zbiera dane okresu istnienia alokacji i obiektu pamięci.<br /><br /> Wartość domyślna `Type` jest **alokacji**.|  
|**/ Porada** lub **/i**|Dodaje szczegółowe żądania programu ASP.NET i informacje o wywołaniach ADO.NET do danych profilowania. **/ Porada** mogą być używane z pobieranie próbek lub metody instrumentacji, i mogą być używane z **/Memory** opcji.|  
|**/ Output:** `File` lub   **/o:**`File`|Określa ścieżkę i nazwę danych profilowania (. *Vsp*) pliku.|  
|**/ NoWait** lub **/n**|Zwraca polecenie prompt natychmiast dzięki dodatkowe polecenia mogą być używane w oknie wiersza polecenia. Należy wpisać **polecenie VSPerfASPNETCmd/shutdown** w osobnym wierszu polecenia, aby wyłączyć profilowania.|  
|**/ PackSymbols**[: {**na**&#124;**poza**} lub **/p**[: {**na**&#124;**poza**}|Symbole (nazwy funkcji i parametru itp.) są osadzone w danych profilowania (. *Vsp*) pliku.|  
|**/ Shutdown:** `Website`lub   **/d:**`Website`|Włącza profilowanie wyłączone. Użyj jako jedyną opcją, w wierszu polecenia po zakończeniu korzystania z **flagi/nowait** opcji do uruchomienia profilowania, lub jeśli program profilujący zakończy się nieoczekiwanie. Określ ten sam adres url, którego używano w oryginalnym **VSPerfASPNETCmd** polecenia.|  
|`Website`|Adres url witryny sieci Web do profilowania.|  
  
## <a name="see-also"></a>Zobacz także  
 [Szybkie profilowanie za pomocą polecenia VSPerfASPNETCmd witryny sieci web](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)   
 [Aplikacje sieci web ASP.NET profilu](../profiling/command-line-profiling-of-aspnet-web-applications.md)
