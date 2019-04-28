---
title: Tworzenie przenośna profilowania pliki danych z poziomu wiersza polecenia | Dokumentacja firmy Microsoft
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
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63434288"
---
# <a name="creating-portable-profiling-data-files-from-the-command-line"></a>Tworzenie przenośnych plików danych profilowania z wiersza polecenia
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby ułatwić udostępnianie danych ułatwia profilowania, można użyć [VSPerfReport](../profiling/vsperfreport.md) narzędzie wiersza polecenia, aby osadzić symbole dla profilowania do pliku Vsp.  
  
 Można również utworzyć wstępnie przeanalizowany profilowania plik danych (.vsps), który jest mniejszy i jest szybsze ładowanie w środowisku IDE.  
  
> [!NOTE]
> Upewnij się, że pliki symboli (.pdb) są dostępne dla **VSPerfReport**. Aby uzyskać więcej informacji, zobacz [jak: Określanie lokalizacji plików symboli z wiersza polecenia](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md).  
>   
> Aby uzyskać informacje o ścieżce do **VSReport**, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
>   
> Nie można filtrować dane profilowania w pliku .vsps.  
  
### <a name="to-embed-the-symbols-for-a-profiling-run-into-a-profiling-data-vsp-file"></a>Aby osadzić symbole dla profilowania w pliku danych (Vsp) profilowania  
  
- W oknie wiersza polecenia wpisz następujące polecenie:  
  
   \<Ścieżka ><strong>VSPerfReport \<</strong> pliku VSP > **packsymbols**  
  
   Domyślnie plik .vsps nosi nazwę z podstawowej nazwy pliku Vsp. Należy określić nazwę alternatywną, za pomocą **dane wyjściowe** opcji.  
  
### <a name="to-create-a-summary-profiling-data-file"></a>Aby utworzyć plik danych profilowania podsumowania  
  
- W oknie wiersza polecenia wpisz następujące polecenie:  
  
   \<Ścieżka ><strong>VSPerfReport \<</strong> pliku VSP > **/summaryfile** [**/Output:**\<nazwa pliku >]  
  
   Domyślnie plik .vsps nosi nazwę z podstawowej nazwy pliku Vsp. Należy określić nazwę alternatywną, za pomocą **dane wyjściowe** opcji.
