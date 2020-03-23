---
title: VSPerfASPNetCmd | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling tools,VSPerfASPNETCmd
- VSPerfASPNETCmd
ms.assetid: f9e9f895-57bb-41e8-8bd1-cdaa738ec220
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 8c9bf465b4da7f305e97a18099a7e27db8eab6b4
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778014"
---
# <a name="vsperfaspnetcmd"></a>VSPerfASPNetCmd
Narzędzie wiersza polecenia **VSPerfASPNetCmd.exe** umożliwia profilowanie ASP.Net witryn sieci Web bez konieczności ustawiania zmiennych środowiskowych lub ponownego uruchamiania komputera. Użyj **vsPerfASPNetCmd.exe** zamiast [VSPerfCmd](../profiling/vsperfcmd.md) podczas profilowania ASP.NET witrynach sieci Web i nie potrzebujesz dodatkowych funkcji oferowanych przez **VSPerfCmd**. Aby uzyskać więcej informacji na temat **programu VSPerfASPNetCmd,** zobacz [Szybkie profilowanie witryny sieci Web za pomocą programu VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md). **VSPerfASPNetCmd** jest preferowanym narzędziem wiersza polecenia do użycia podczas korzystania z autonomicznego profilera do profilowania witryny sieci Web ASP.NET.

## <a name="syntax"></a>Składnia
 **vsperfaspnetcmd** [/*Opcje*] *Strona internetowa*

## <a name="options"></a>Opcje

|Opcja|Opis|
|------------|-----------------|
|**/Próbka** lub **/s**|Profile na stronie internetowej przy użyciu metody próbkowania. **/Sample** jest metodą domyślną. /Próbki nie można używać z **/Trace**.|
|**/Trace** lub **/t**|profili za pomocą metody instrumentacji. /Trace nie można używać z **/Sample**.|
|**/Memory**[**:**`Type`]lub **/m**[**:**{**a**&#124;**l**}]|Profile alokacji pamięci i opcjonalnie profile istnienia obiektu (wyrzucanie elementów bezużytecznych). **/Pamięć** może być używana z próbkowaniem lub metodą oprzyrządowania.<br /><br /> *Typ* może być jedną z następujących czynności:<br /><br /> -   **alokacji** (lub **a)** zbiera tylko dane alokacji pamięci.<br />-   **okres istnienia** (lub **l**) zbiera alokacji pamięci i danych okresu istnienia obiektu.<br /><br /> Wartością `Type` domyślną jest **alokacja**.|
|**/Wskazówka** lub **/i**|Dodaje szczegółowe żądania ASP.NET i ADO.NET informacje wywołania do danych profilowania. **/Tip** może być używany z próbkowaniem lub metodą oprzyrządowania i może być używany z opcją **/Memory.**|
|**/Wyjście:** `File` lub **/o:**`File`|Określa ścieżkę i nazwę pliku danych profilowania (.* vsp).*|
|**/NoWait** lub **/n**|Natychmiast zwraca wiersz polecenia, aby w oknie wiersza polecenia można było użyć dodatkowych poleceń. Aby wyłączyć profilowanie, należy **wpisać polecenie VSPerfASPNETCmd /Shutdown** w osobnym wierszu polecenia.|
|**/PackSymbols**[:{**na**&#124;**wyłączony**}lub **/p**[:{**przy**&#124;**wyłączony**}|Osadza symbole (nazwy funkcji i parametrów itp.) w danych profilowania (.* vsp).*|
|**/Shutdown:** `Website`lub **/d:**`Website`|Wyłącza profilowanie. Użyj jako jedynej opcji w wierszu polecenia po użyciu opcji **/NoWait,** aby rozpocząć profilowanie lub jeśli profiler kończy się nieoczekiwanie. Określ ten sam adres URL, który był używany w oryginalnym poleceniu **VSPerfASPNETCmd.**|
|`Website`|Adres URL strony internetowej, która ma być profilowana.|

## <a name="see-also"></a>Zobacz też
- [Szybkie profilowanie witryny sieci Web za pomocą vsperfAspnetcmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)
- [Profil ASP.NET aplikacji internetowych](../profiling/command-line-profiling-of-aspnet-web-applications.md)
