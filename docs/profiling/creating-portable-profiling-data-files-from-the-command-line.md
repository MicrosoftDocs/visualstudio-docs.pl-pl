---
title: Tworzenie plików danych profilowania przenośnego z wiersza polecenia | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 2ceb63a7-b835-4988-b756-2afc3fcc4808
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 8caa1a4976da39b155edde36d538ca193bd1addd
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779496"
---
# <a name="create-portable-profiling-data-files-from-the-command-line"></a>Tworzenie przenośnych plików danych profilowania z wiersza polecenia
Aby ułatwić udostępnianie danych profilowania, można użyć narzędzia wiersza polecenia [VSPerfReport,](../profiling/vsperfreport.md) aby osadzić symbole profilowania w pliku . *vsp.*

 Można również utworzyć wstępnie przeanalizowane dane profilowania (.* vsps)* plik, który jest mniejszy i szybciej załadować w IDE.

> [!NOTE]
> Upewnij się, że symbol (.* pdb*) pliki są dostępne dla **VSPerfReport**. Aby uzyskać więcej informacji, zobacz [Jak: Określanie lokalizacji plików symboli z wiersza polecenia](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md).
>
> Aby uzyskać informacje o ścieżce do **vsreport,** zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).
>
> Dane profilowania w . nie można filtrować pliku *vsps.*

### <a name="to-embed-the-symbols-for-a-profiling-run-into-a-profiling-data-vsp-file"></a>Aby osadzić symbole profilowania, można uzyskać dane profilowania (.* vsp*) plik

- W oknie wiersza polecenia wpisz następujące polecenie:

   \<Ścieżka>> pliku <strong>VSPerfReport \< </strong>VSP **/PackSymbols**

   Domyślnie plik . plik *vsps* nosi nazwę podstawową pliku . *vsp.* Alternatywną nazwę można określić za pomocą opcji **Wyjście.**

### <a name="to-create-a-summary-profiling-data-file"></a>Aby utworzyć plik danych profilowania podsumowania

- W oknie wiersza polecenia wpisz następujące polecenie:

   \<Ścieżka>> pliku <strong>VSPERF \<VSP </strong> **/SummaryFile** [**/Output:**\<Nazwa pliku>]

   Domyślnie plik . plik *vsps* nosi nazwę podstawową pliku . *vsp.* Alternatywną nazwę można określić za pomocą opcji **Wyjście.**
