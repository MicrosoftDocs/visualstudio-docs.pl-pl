---
title: VSPerfASPNetCmd | Microsoft Docs
description: Dowiedz się, jak narzędzie wiersza polecenia VSPerfASPNetCmd.exe umożliwia profilowanie witryn sieci Web ASP.Net bez konieczności ustawiania zmiennych środowiskowych lub ponownego uruchamiania komputera.
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- profiling tools,VSPerfASPNETCmd
- VSPerfASPNETCmd
ms.assetid: f9e9f895-57bb-41e8-8bd1-cdaa738ec220
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 1d886284a130d9c103d2f0d8a6bc24d2ebd69b6e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99911623"
---
# <a name="vsperfaspnetcmd"></a>VSPerfASPNetCmd
Narzędzie wiersza polecenia **VSPerfASPNetCmd.exe** umożliwia profilowanie witryn sieci Web ASP.NET bez konieczności ustawiania zmiennych środowiskowych lub ponownego uruchomienia komputera. Użyj **VSPerfASPNetCmd.exe** zamiast [VSPerfCmd](../profiling/vsperfcmd.md) podczas profilowania witryn sieci Web ASP.NET i nie potrzebujesz dodatkowych funkcji udostępnianych przez **VSPerfCmd**. Aby uzyskać więcej informacji na temat **VSPerfASPNETCmd**, zobacz [szybkie profilowanie witryny sieci Web za pomocą usługi VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md). **VSPerfASPNETCmd** jest preferowanym narzędziem wiersza polecenia do użycia w przypadku korzystania z autonomicznego profilera do profilowania witryny sieci Web ASP.NET.

## <a name="syntax"></a>Składnia
 **VSPerfASPNETCmd** [/*Options*] — *Witryna sieci Web*

## <a name="options"></a>Opcje

|Opcja|Opis|
|------------|-----------------|
|**/Sample** lub   **/s**|Witryna sieci Web profilów przy użyciu metody próbkowania. **/Sample** jest metodą domyślną. /Sample nie można używać z **/Trace**.|
|**/Trace** lub   **/t**|Witryna sieci Web profilów przy użyciu metody instrumentacji. /Trace nie można używać z **/Sample**.|
|**/Memory**[**:** `Type` ] lub **/m**[**:**{**a**&#124;**l**}]|Profile alokacji pamięci i opcjonalne profile okresy istnienia obiektu (odzyskiwanie pamięci). **/Memory** można użyć z próbką lub metodą Instrumentacji.<br /><br /> *Typ* może być jednym z następujących:<br /><br /> -   **alokacja** (lub **a**) zbiera tylko dane alokacji pamięci.<br />-   **okres istnienia** (lub **l**) zbiera dane alokacji pamięci i okresu istnienia obiektu.<br /><br /> Wartość domyślna `Type` to **alokacja**.|
|**/TIP** lub   **/i**|Dodaje szczegółowe informacje o żądaniu ASP.NET i wywołaniu ADO.NET do danych profilowania. **/TIP** może być używana z próbką lub Instrumentacją i może być używana z opcją **/Memory** .|
|**/Output:** `File` lub   **/o:**`File`|Określa ścieżkę i nazwę pliku danych profilowania (.*VSP*).|
|**Flagi/nowait** lub   **/n**|Zwraca wiersz polecenia natychmiast, aby można było użyć dodatkowych poleceń w oknie wiersza polecenia. Aby wyłączyć profilowanie, należy wpisać **VSPerfASPNETCmd/Shutdown** w osobnym wierszu polecenia.|
|**/PackSymbols**[: {**na**&#124;**off**} lub   **/p**[: {**on**&#124;**off**}|Osadza symbole (nazwy funkcji i parametrów itp.) w danych profilowania (.*VSP*).|
|**/Shutdown:** `Website` lub   **/d:**`Website`|Wyłącza profilowanie. Użyj jako jedynej opcji w wierszu polecenia po użyciu opcji **flagi/nowait** , aby rozpocząć profilowanie, lub jeśli Profiler się nieoczekiwanie skończy. Określ ten sam adres URL, który został użyty w oryginalnym **VSPerfASPNETCmd** polecenia.|
|`Website`|Adres URL witryny sieci Web, która ma zostać profilowana.|

## <a name="see-also"></a>Zobacz też
- [Szybkie profilowanie witryny sieci Web za pomocą VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)
- [Profilowanie aplikacji sieci Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
