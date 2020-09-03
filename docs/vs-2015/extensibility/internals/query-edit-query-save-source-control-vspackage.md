---
title: Zapytanie edycji zapytania Save (pakietu VSPackage kontroli źródła) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- QEQS events
- Query Edit Query Save events
- source control packages, Query Edit Query Save events
ms.assetid: c360d2ad-fe42-4d65-899d-d1588cc8a322
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2ad0cf7c3e1d3269dbe7ebee051cc32e2e8531ef
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148889"
---
# <a name="query-edit-query-save-source-control-vspackage"></a>Edytowanie i zapisywanie zapytań (pakiet VSPackage kontroli kodu źródłowego)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Edytory mogą emitować zdarzenia edycji zapytania Save (QEQS). [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Procedura wejścia kontroli źródła implementuje usługę QEQS, tak aby była odbiorcą zdarzeń QEQS. Te zdarzenia są następnie delegowane do aktualnie aktywnej kontroli źródła pakietu VSPackage. Aktywna pakietu VSPackage kontroli źródła implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> metody i. Metody `IVsQueryEditQuerySave2` interfejsu są zwykle wywoływane bezpośrednio przed rozpoczęciem edycji dokumentu po raz pierwszy i bezpośrednio przed zapisaniem dokumentu.  
  
## <a name="queryeditquerysave-events"></a>Zdarzenia QueryEditQuerySave  
 Pakietu VSPackage kontroli źródła musi obsługiwać zdarzenia QEQS przez implementację `IVsQueryEditQuerySave2` interfejsu i niezbędnych metod. Poniżej znajduje się krótki opis dwóch metod, które pakietu VSPackage muszą zaimplementować co najmniej. Rzeczywista implementacja musi być zgodna z logiką modelu kontroli źródła.  
  
### <a name="queryeditfiles-method"></a>QueryEditFiles, Metoda  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>Jest wywoływana, gdy dowolny projekt lub Edytor chce zmodyfikować plik. W idealnym przypadku ta metoda jest wywoływana *przed* zmodyfikowaniem pliku i po jego zapisaniu. Po wywołaniu `IVsQueryEditQuerySave2::QueryEditFiles` Metoda sprawdza, czy dane znajdują się pod kontrolą źródła, czy muszą zostać wyewidencjonowane, oraz czy można je ponownie załadować. Jeśli w okolicznościach nie można edytować plików, `IVsQueryEditQuerySave2::QueryEditFiles` Metoda nakazuje programowi wywołującemu anulowanie edycji. Istnieje również możliwość określenia trybu wywołania przez obiekt wywołujący. W trybie dyskretnym ta metoda wykonuje akcję tylko wtedy, gdy nie powoduje wyświetlania żadnego interfejsu użytkownika. Jeśli nie można uniknąć tego interfejsu, należy zwrócić flagę w celu wskazania problemu.  
  
 Metoda zachowuje się w sposób transakcyjny; oznacza to, że jeśli Edycja zostanie anulowana w jednym pliku, Edycja zostanie anulowana dla wszystkich plików. Na odwrót, jeśli Edycja jest dozwolona, jest dozwolona dla wszystkich plików. Jeśli ta metoda umożliwia edytowanie jednokrotne dla danego zestawu plików, musi zawsze zezwalać na edycję w kolejnych wywołaniach dla tego samego zestawu plików. Pętla zezwalania na edycję będzie kontynuowana do momentu zamknięcia, zapisania i ponownego załadowania plików; do momentu zmiany atrybutów (właściwości); lub do momentu zmiany pakietu kontroli źródła. Przypadki, które należy wziąć pod uwagę podczas implementowania `IVsQueryEditQuerySave2::QueryEditFiles` metody, obejmują wiele plików, pliki specjalne, anulowanie z użytkownika i edycję w pamięci.  
  
### <a name="querysavefiles-method"></a>QuerySaveFiles, Metoda  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>Jest wywoływana, gdy dowolny projekt lub Edytor wymaga zapisania zestawu plików. Po wywołaniu `IVsQueryEditQuerySave2::QuerySaveFiles` Metoda sprawdza, czy te pliki są tylko do odczytu i czy znajdują się pod kontrolą źródła. Jeśli pliki wymagają wyewidencjonowania, wywołanie jest delegowane do pakietu kontroli źródła. Jeśli okoliczności uniemożliwiają zapisywanie plików, `IVsQueryEditQuerySave2::QuerySaveFiles` Metoda musi poinformować Edytor, aby anulować operację zapisywania. Podobnie jak w przypadku `IVsQueryEditQuerySave2::QueryEditFiles` metody obiekt wywołujący może określić tryb wywoływania. W trybie dyskretnym ta metoda wykonuje akcję tylko wtedy, gdy nie powoduje wyświetlania żadnego interfejsu użytkownika. Jeśli nie można uniknąć tego interfejsu, należy zwrócić flagę w celu wskazania problemu.  
  
 Ta metoda musi działać w sposób transakcyjny; oznacza to, że jeśli zapis zostanie anulowany w jednym pliku, operacja zapisywania zostanie anulowana dla wszystkich plików. Z drugiej strony, jeśli zapis jest dozwolony, musi być dozwolony dla wszystkich plików. Podobnie jak w przypadku `IVsQueryEditQuerySave2::QueryEditFiles` metody, przypadki, które należy wziąć pod uwagę podczas implementowania `IVsQueryEditQuerySave2::QuerySaveFiles` metody, obejmują wiele plików, pliki specjalne, anulowanie z użytkownika i edycję w pamięci.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
