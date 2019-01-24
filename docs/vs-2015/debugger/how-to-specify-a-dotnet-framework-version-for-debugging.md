---
title: 'Instrukcje: Określanie wersji programu .NET Framework do debugowania | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- .NET Framework, specifying version for debugging
- debugging [Visual Studio], specifying .NET Framework version
ms.assetid: 7a4893ba-4620-4774-893f-378d4ca28893
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5b3e5d7ebb1f61ffdbff98f49f83025115c80f64
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54771260"
---
# <a name="how-to-specify-a-net-framework-version-for-debugging"></a>Instrukcje: Określanie wersji programu .NET Framework do debugowania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] Debuger obsługuje debugowanie starszych wersji programu Microsoft [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] oraz bieżącej wersji. W przypadku uruchomienia aplikacji w programie Visual Studio, debuger zawsze można zidentyfikować poprawną wersję [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] dla aplikacji jest debugowany. Jeśli aplikacja jest już uruchomiona, a używasz **dołączyć do**, debuger może nie zawsze można zidentyfikować starszą wersję [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. Jeśli tak się stanie, zostanie wyświetlony komunikat o błędzie informujący, że,  
  
 Debuger podejścia biznesowego uczyniło nieprawidłowe założenie dotyczące [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] wersji aplikacji zamierza użyć.  
  
 W tych rzadkich przypadkach można ustawić klucz rejestru, aby wskazać do debugera w wyborze wersji do użycia.  
  
### <a name="to-specify-a-net-framework-version-for-debugging"></a>Aby określić wersji programu .NET Framework do debugowania  
  
1.  Szukaj w katalogu Windows\Microsoft.NET\Framework można znaleźć wersji .NET Framework zainstalowanej na komputerze. Numery wersji wyglądać mniej więcej tak:  
  
     `V1.1.4322`  
  
     Określ liczbę poprawnej wersji i zanotuj ją.  
  
2.  Rozpocznij **Edytora rejestru** (regedit).  
  
3.  W **Edytora rejestru**, otwórz folder, w kluczu HKEY_LOCAL_MACHINE.  
  
4.  Przejdź do: HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine\\{449EC4CC-30D2-4032-9256-EE18EB41B62B}  
  
     Jeśli klucz nie istnieje, kliknij prawym przyciskiem myszy HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine i kliknij **nowy klucz**. Nazwij nowy klucz `{449EC4CC-30D2-4032-9256-EE18EB41B62B}`.  
  
5.  Po przejściu do {449EC4CC-30D2-4032-9256-EE18EB41B62B}, Szukaj w **nazwa** kolumny i Znajdź klucz CLRVersionForDebugging.  
  
    1.  Jeśli klucz nie istnieje, kliknij prawym przyciskiem myszy {449EC4CC-30D2-4032-9256-EE18EB41B62B} i kliknij przycisk **nową wartość ciągu**. Kliknij prawym przyciskiem myszy nową wartość ciągu, kliknij przycisk **Zmień nazwę**i wpisz `CLRVersionForDebugging`.  
  
6.  Kliknij dwukrotnie **CLRVersionForDebugging**.  
  
7.  W **Edytowanie ciągu** wpisz numer wersji .NET Framework w **wartość** pole. Na przykład: V1.1.4322  
  
8.  Kliknij przycisk **OK**.  
  
9. Zamknij **Edytora rejestru**.  
  
     Jeśli nadal otrzymujesz komunikat o błędzie podczas uruchamiania debugowania, upewnij się, że wprowadzony numer wersji, który jest poprawnie w rejestrze. Sprawdź także, że używasz wersji [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] obsługiwane przez program Visual Studio. Debuger jest zgodny z bieżącen wersji .NET Framework i poprzednich wersji, ale może nie być zgodny wprzód z przyszłych wersji.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawienia debugera i przygotowanie](../debugger/debugger-settings-and-preparation.md)
