---
title: Zapytanie edycji zapytania Save (pakietu VSPackage kontroli źródła) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- QEQS events
- Query Edit Query Save events
- source control packages, Query Edit Query Save events
ms.assetid: c360d2ad-fe42-4d65-899d-d1588cc8a322
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: be12297bdaeb112d7421b02da1153ed62d6d14f8
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72724772"
---
# <a name="query-edit-query-save-source-control-vspackage"></a>Edytowanie i zapisywanie zapytań (pakiet VSPackage kontroli kodu źródłowego)
Edytory [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] mogą emitować zdarzenia edycji zapytania Save (QEQS). [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] stub kontroli źródła implementuje usługę QEQS, tak aby była odbiorcą zdarzeń QEQS. Te zdarzenia są następnie delegowane do aktualnie aktywnej kontroli źródła pakietu VSPackage. Aktywna pakietu VSPackage kontroli źródła implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> i jej metody. Metody interfejsu `IVsQueryEditQuerySave2` są zwykle wywoływane bezpośrednio przed edytowaniem dokumentu po raz pierwszy i bezpośrednio przed zapisaniem dokumentu.

## <a name="queryeditquerysave-events"></a>Zdarzenia QueryEditQuerySave
 Pakietu VSPackage kontroli źródła musi obsługiwać zdarzenia QEQS przez implementację interfejsu `IVsQueryEditQuerySave2` i niezbędnych metod. Poniżej znajduje się krótki opis dwóch metod, które pakietu VSPackage muszą zaimplementować co najmniej. Rzeczywista implementacja musi być zgodna z logiką modelu kontroli źródła.

### <a name="queryeditfiles-method"></a>QueryEditFiles, Metoda
 @No__t_0 jest wywoływana, gdy dowolny projekt lub Edytor chce zmodyfikować plik. W idealnym przypadku ta metoda jest wywoływana *przed* zmodyfikowaniem pliku i po jego zapisaniu. Po wywołaniu metoda `IVsQueryEditQuerySave2::QueryEditFiles` sprawdza, czy dane znajdują się pod kontrolą źródła, czy muszą zostać wyewidencjonowane, oraz czy można je ponownie załadować. Jeśli nie można edytować plików, Metoda `IVsQueryEditQuerySave2::QueryEditFiles` informuje program wywołujący, aby anulował edycję. Istnieje również możliwość określenia trybu wywołania przez obiekt wywołujący. W trybie dyskretnym ta metoda wykonuje akcję tylko wtedy, gdy nie powoduje wyświetlania żadnego interfejsu użytkownika. Jeśli nie można uniknąć tego interfejsu, należy zwrócić flagę w celu wskazania problemu.

 Metoda zachowuje się w sposób transakcyjny; oznacza to, że jeśli Edycja zostanie anulowana w jednym pliku, Edycja zostanie anulowana dla wszystkich plików. Na odwrót, jeśli Edycja jest dozwolona, jest dozwolona dla wszystkich plików. Jeśli ta metoda umożliwia edytowanie jednokrotne dla danego zestawu plików, musi zawsze zezwalać na edycję w kolejnych wywołaniach dla tego samego zestawu plików. Pętla zezwalania na edycję będzie kontynuowana do momentu zamknięcia, zapisania i ponownego załadowania plików; do momentu zmiany atrybutów (właściwości); lub do momentu zmiany pakietu kontroli źródła. Przypadki, do których należy wziąć pod uwagę wdrożenie metody `IVsQueryEditQuerySave2::QueryEditFiles`, obejmują wiele plików, pliki specjalne, anulowanie z użytkownika i edycję w pamięci.

### <a name="querysavefiles-method"></a>QuerySaveFiles, Metoda
 @No__t_0 jest wywoływana, gdy dowolny projekt lub Edytor muszą zapisać zestaw plików. Gdy jest wywoływana, Metoda `IVsQueryEditQuerySave2::QuerySaveFiles` sprawdza, czy dany plik jest tylko do odczytu i czy znajduje się pod kontrolą źródła. Jeśli pliki wymagają wyewidencjonowania, wywołanie jest delegowane do pakietu kontroli źródła. Jeśli nie ma możliwości zapisania plików, Metoda `IVsQueryEditQuerySave2::QuerySaveFiles` musi poinformować Edytor, aby anulował zapisywanie. Podobnie jak w przypadku metody `IVsQueryEditQuerySave2::QueryEditFiles`, możliwe jest określenie trybu wywołania przez obiekt wywołujący. W trybie dyskretnym ta metoda wykonuje akcję tylko wtedy, gdy nie powoduje wyświetlania żadnego interfejsu użytkownika. Jeśli nie można uniknąć tego interfejsu, należy zwrócić flagę w celu wskazania problemu.

 Ta metoda musi działać w sposób transakcyjny; oznacza to, że jeśli zapis zostanie anulowany w jednym pliku, operacja zapisywania zostanie anulowana dla wszystkich plików. Z drugiej strony, jeśli zapis jest dozwolony, musi być dozwolony dla wszystkich plików. Podobnie jak w przypadku metody `IVsQueryEditQuerySave2::QueryEditFiles`, sytuacje, w których należy wziąć pod uwagę implementację metody `IVsQueryEditQuerySave2::QuerySaveFiles`, obejmują wiele plików, pliki specjalne, anulowanie z użytkownika i edycję w pamięci.

## <a name="see-also"></a>Zobacz także
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>