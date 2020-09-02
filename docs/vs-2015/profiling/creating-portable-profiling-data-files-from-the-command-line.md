---
title: Tworzenie przenośnych plików danych profilowania z wiersza polecenia | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 2ceb63a7-b835-4988-b756-2afc3fcc4808
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5d343392c9e554c5e51325964949cd3ea13237b8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64791228"
---
# <a name="creating-portable-profiling-data-files-from-the-command-line"></a>Tworzenie przenośnych plików danych profilowania z wiersza polecenia
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby ułatwić udostępnianie danych profilowania, można użyć narzędzia wiersza polecenia [VSPerfReport](../profiling/vsperfreport.md) do osadzenia symboli dla uruchomienia profilowania w pliku. vsp.  
  
 Możesz również utworzyć wstępnie przeanalizowany plik danych profilowania (vsps), który jest krótszy i jest szybszy do załadowania w środowisku IDE.  
  
> [!NOTE]
> Upewnij się, że pliki symboli (. pdb) są dostępne dla **VSPerfReport**. Aby uzyskać więcej informacji, zobacz [How to: Określanie lokalizacji plików symboli w wierszu polecenia](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md).  
>   
> Aby uzyskać informacje o ścieżce do **VSReport**, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
>   
> Nie można filtrować danych profilowania w pliku. vsps.  
  
### <a name="to-embed-the-symbols-for-a-profiling-run-into-a-profiling-data-vsp-file"></a>Aby osadzić symbole do uruchomienia profilowania do pliku danych profilowania (. vsp)  
  
- W oknie wiersza polecenia wpisz następujące polecenie:  
  
   \<Path><strong>\<</strong>Plik VSP VSPerfReport> **/PackSymbols**  
  
   Domyślnie plik. vsps jest nazwany nazwą podstawową pliku. vsp. Możesz określić alternatywną nazwę przy użyciu opcji **wyjście** .  
  
### <a name="to-create-a-summary-profiling-data-file"></a>Aby utworzyć podsumowujący plik danych profilowania  
  
- W oknie wiersza polecenia wpisz następujące polecenie:  
  
   \<Path><strong>\<</strong>Plik VSP VSPerfReport> **/SummaryFile** [**/Output:** \<File Name> ]  
  
   Domyślnie plik. vsps jest nazwany nazwą podstawową pliku. vsp. Możesz określić alternatywną nazwę przy użyciu opcji **wyjście** .
