---
title: Uwidacznianie typów dla projektantów wizualizacji | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- types [Visual Studio SDK], exposing to visual designers
- designers [Visual Studio SDK], exposing types
- custom tools, exposing types to visual designers
ms.assetid: a7a32ad4-3a0a-4eb8-a6ac-491c42885639
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f4d6c0e163b751f1873fdb941e85c273dcc4fde5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65691201"
---
# <a name="exposing-types-to-visual-designers"></a>Udostępnianie typów dla projektantów wizualnych
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Aby można było wyświetlić projektanta wizualnego, musi mieć dostęp do definicji klas i typów w czasie projektowania. Klasy są ładowane ze wstępnie zdefiniowanego zestawu zestawów, który obejmuje kompletny zestaw zależności bieżącego projektu (odwołania i ich zależności). Może być również konieczne, aby projektanci wizualizacji mogli uzyskiwać dostęp do klas i typów, które są zdefiniowane w plikach generowanych przez narzędzia niestandardowe.  
  
 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] [!INCLUDE[csprcs](../../includes/csprcs-md.md)] Systemy projektów i zapewniają obsługę uzyskiwania dostępu do wygenerowanych klas i typów za pomocą tymczasowych przenośnych plików wykonywalnych (tymczasowych PES). Dowolny plik wygenerowany przez narzędzie niestandardowe można skompilować do tymczasowego zestawu, tak aby typy mogły być ładowane z tych zestawów i udostępniane projektantom. Dane wyjściowe każdego narzędzia niestandardowego są kompilowane w oddzielnym tymczasowym środowisku PE, a powodzenie lub niepowodzenie tej tymczasowej kompilacji zależy tylko od tego, czy wygenerowany plik można skompilować. Mimo że projekt nie może być kompilowany jako całość, poszczególne tymczasowe elementu PEs mogą nadal być dostępne dla projektantów.  
  
 System projektu zapewnia pełną obsługę śledzenia zmian w pliku wyjściowym niestandardowego narzędzia, pod warunkiem, że te zmiany są wynikiem uruchamiania niestandardowego narzędzia. Za każdym razem, gdy uruchamiane jest narzędzie niestandardowe, zostaje wygenerowany nowy tymczasowy środowisko uruchomieniowe oraz odpowiednie powiadomienia są wysyłane do projektantów.  
  
> [!NOTE]
> Ponieważ plik tymczasowej generacji pliku wykonywalnego programu jest w tle, żadne błędy nie są zgłaszane użytkownikowi, jeśli kompilacja zakończy się niepowodzeniem.  
  
 Niestandardowe narzędzia wykorzystujące tymczasową obsługę środowiska PE muszą być zgodne z następującymi regułami:  
  
- `GeneratesDesignTimeSource` w rejestrze musi być ustawiona wartość 1.  
  
     Nie jest wykonywana kompilacja pliku wykonywalnego programu bez tego ustawienia.  
  
- Wygenerowany kod musi znajdować się w tym samym języku co globalne ustawienie projektu.  
  
     Tymczasowy środowisko PE jest kompilowane niezależnie od tego, co narzędzie niestandardowe raportuje jako żądane rozszerzenie <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A> , które `GeneratesDesignTimeSource` zostało ustawione na 1 w rejestrze. Rozszerzenie nie musi być. vb,. cs lub. JSL; może to być dowolne rozszerzenie.  
  
- Kod wygenerowany przez narzędzie niestandardowe musi być prawidłowy i musi kompilować się we własnym zakresie przy użyciu tylko zestawu odwołań obecnych w projekcie w momencie <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> zakończenia wykonywania.  
  
     Po skompilowaniu tymczasowego środowiska PE jedynym plikiem źródłowym dostarczonym do kompilatora jest dane wyjściowe niestandardowego narzędzia. W związku z tym narzędzie niestandardowe, które używa tymczasowego środowiska PE, musi generować pliki wyjściowe, które mogą być kompilowane niezależnie od innych plików w projekcie.  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do obiektu BuildManager](https://msdn.microsoft.com/50080ec2-c1c9-412c-98ef-18d7f895e7fa)   
 [Implementowanie generatorów pojedynczych plików](../../extensibility/internals/implementing-single-file-generators.md)   
 [Określanie domyślnej przestrzeni nazw projektu](../../misc/determining-the-default-namespace-of-a-project.md)   
 [Rejestrowanie generatorów jednoplikowych](../../extensibility/internals/registering-single-file-generators.md)
