---
title: Kwerenda Edytuj kwerendę Zapisz (Formant źródła VSPackage) | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- QEQS events
- Query Edit Query Save events
- source control packages, Query Edit Query Save events
ms.assetid: c360d2ad-fe42-4d65-899d-d1588cc8a322
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c09ac0cb4f51b8f2484b95d403ff6d0445631479
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705961"
---
# <a name="query-edit-query-save-source-control-vspackage"></a>Edytowanie i zapisywanie zapytań (pakiet VSPackage kontroli kodu źródłowego)
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]edytory mogą emitować zdarzenia zapisywania zapytań (QEQS). [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Source Control Stub implementuje usługę QEQS, dzięki czemu jest odbiorcą zdarzeń QEQS. Zdarzenia te są następnie delegowane do aktualnie aktywnej kontroli źródła VSPackage. Active source control VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> implementuje i jego metody. Metody `IVsQueryEditQuerySave2` interfejsu są zazwyczaj wywoływane bezpośrednio przed edycją dokumentu po raz pierwszy i bezpośrednio przed zapisaniem dokumentu.

## <a name="queryeditquerysave-events"></a>Zdarzenia QueryEditQuerySave
 Formant źródła VSPackage musi obsługiwać zdarzenia QEQS implementując `IVsQueryEditQuerySave2` interfejs i niezbędne metody. Poniżej znajduje się krótki opis dwóch metod, które VSPackage musi implementować co najmniej. Rzeczywista implementacja musi być zgodna z logiką modelu kontroli źródła.

### <a name="queryeditfiles-method"></a>Metoda QueryEditFiles
 Wywoływany <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> jest, gdy dowolny projekt lub edytor chce zmodyfikować plik. W idealnym przypadku ta metoda jest wywoływana *przed* modyfikacją pliku i zapisaniem pliku. Po wywołaniu `IVsQueryEditQuerySave2::QueryEditFiles` metoda sprawdza, czy dane pliki są pod kontrolą źródła, czy muszą być wyewidencjonowane i czy można je ponownie załadować. Jeśli okoliczności uniemożliwiają edytowanie plików, `IVsQueryEditQuerySave2::QueryEditFiles` metoda nakazuje programowi wywołującemu anulowanie edycji. Jest również możliwe dla obiektu wywołującego, aby określić tryb wywołania. W trybie "cichy" ta metoda wykonuje akcję tylko wtedy, gdy nie powoduje żadnych interfejsu użytkownika. Jeśli interfejs użytkownika jest nieuniknione, flaga musi zostać zwrócona, aby wskazać problem.

 Metoda zachowuje się w sposób transakcyjny; oznacza to, że jeśli edycja zostanie anulowana w jednym pliku, edycja zostanie anulowana dla wszystkich plików. Z drugiej strony, jeśli edycja jest dozwolona, jest dozwolona dla wszystkich plików. Jeśli ta metoda umożliwia edycję raz dla danego zestawu plików, musi zawsze zezwalać na edytowanie kolejnych wywołań dla tego samego zestawu plików. Pętla zezwalania na edycję jest kontynuowana, dopóki pliki nie zostaną zamknięte, zapisane i ponownie załadowane; aż do zmiany ich atrybutów (właściwości); lub do momentu zmiany pakietu kontroli źródła. Przypadki, które należy `IVsQueryEditQuerySave2::QueryEditFiles` wziąć pod uwagę podczas implementacji metody obejmują wiele plików, pliki specjalne, anulowanie od użytkownika i edycje w pamięci.

### <a name="querysavefiles-method"></a>Metoda QuerySaveFiles
 Wywoływany <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> jest, gdy dowolny projekt lub edytor musi zapisać zestaw plików. Po wywołaniu `IVsQueryEditQuerySave2::QuerySaveFiles` metoda sprawdza, czy dane pliki są tylko do odczytu i czy są one pod kontrolą źródła. Jeśli pliki muszą być wyewidencjonowane, wywołanie jest delegowane do pakietu kontroli źródła. Jeśli okoliczności uniemożliwiają zapisywanie plików, `IVsQueryEditQuerySave2::QuerySaveFiles` metoda musi poinformować edytora, aby anulować zapisywanie. Podobnie jak `IVsQueryEditQuerySave2::QueryEditFiles` w przypadku metody, jest możliwe dla wywołującego, aby określić tryb wywołania. W trybie "cichy" ta metoda wykonuje akcję tylko wtedy, gdy nie powoduje żadnych interfejsu użytkownika. Jeśli interfejs użytkownika jest nieuniknione, flaga musi zostać zwrócona, aby wskazać problem.

 Ta metoda musi zachowywać się w sposób transakcyjny; oznacza to, że jeśli zapis zostanie anulowany w jednym pliku, zapis zostanie anulowany dla wszystkich plików. Z drugiej strony, jeśli zapis jest dozwolony, musi być dozwolony dla wszystkich plików. Podobnie jak `IVsQueryEditQuerySave2::QueryEditFiles` w przypadku metody, przypadki, które należy wziąć pod uwagę podczas implementacji `IVsQueryEditQuerySave2::QuerySaveFiles` metody obejmują wiele plików, pliki specjalne, anulować od użytkownika i edycje w pamięci.

## <a name="see-also"></a>Zobacz też
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
