---
title: Profilowanie wiersza polecenia — Tworzenie przenośnych plików danych
description: Aby ułatwić udostępnianie danych profilowania, użyj narzędzia wiersza polecenia VSPerfReport.exe, aby osadzić symbole dla uruchomienia profilowania w pliku. vsp.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 2ceb63a7-b835-4988-b756-2afc3fcc4808
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 5df9f14fecce23eb72d08dcba87dee360269e078
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2021
ms.locfileid: "98718970"
---
# <a name="create-portable-profiling-data-files-from-the-command-line"></a>Tworzenie przenośnych plików danych profilowania z wiersza polecenia
Aby ułatwić udostępnianie danych profilowania, można użyć narzędzia wiersza polecenia [VSPerfReport](../profiling/vsperfreport.md) do osadzenia symboli do uruchomienia profilowania. plik *VSP* .

 Możesz również utworzyć wstępnie przeanalizowane dane profilowania (.*vsps*) plik, który jest mniejszy i jest szybszy do załadowania w środowisku IDE.

> [!NOTE]
> Upewnij się, że symbol (.*PDB*) są dostępne dla **VSPerfReport**. Aby uzyskać więcej informacji, zobacz [How to: Określanie lokalizacji plików symboli w wierszu polecenia](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md).
>
> Aby uzyskać informacje o ścieżce do **VSReport**, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).
>
> Dane profilowania w. nie można filtrować pliku *vsps* .

### <a name="to-embed-the-symbols-for-a-profiling-run-into-a-profiling-data-vsp-file"></a>Aby osadzić symbole dla profilowania uruchamiania w danych profilowania (.*VSP*), plik

- W oknie wiersza polecenia wpisz następujące polecenie:

   \<Path><strong>\<</strong>Plik VSP VSPerfReport> **/PackSymbols**

   Domyślnie. plik *vsps* ma nazwę bazową. plik *VSP* . Możesz określić alternatywną nazwę przy użyciu opcji **wyjście** .

### <a name="to-create-a-summary-profiling-data-file"></a>Aby utworzyć podsumowujący plik danych profilowania

- W oknie wiersza polecenia wpisz następujące polecenie:

   \<Path><strong>\<</strong>Plik VSP VSPerfReport> **/SummaryFile** [**/Output:** \<File Name> ]

   Domyślnie. plik *vsps* ma nazwę bazową. plik *VSP* . Możesz określić alternatywną nazwę przy użyciu opcji **wyjście** .
