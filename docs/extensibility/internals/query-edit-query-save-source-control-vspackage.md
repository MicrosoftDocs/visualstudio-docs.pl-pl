---
title: Zapytanie edycji zapytania Save (pakietu VSPackage kontroli źródła) | Microsoft Docs
description: Dowiedz się więcej na temat roli zdarzeń Query-Save Query-Edit i sposobu ich obsługi przez pakietu VSPackage kontroli źródła.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- QEQS events
- Query Edit Query Save events
- source control packages, Query Edit Query Save events
ms.assetid: c360d2ad-fe42-4d65-899d-d1588cc8a322
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9295644a07a1840cd4874b8bfff298ad9d46c928
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105060916"
---
# <a name="query-edit-query-save-source-control-vspackage"></a>Edytowanie i zapisywanie zapytań (pakiet VSPackage kontroli kodu źródłowego)
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Edytory mogą emitować zdarzenia edycji zapytania Save (QEQS). [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Procedura wejścia kontroli źródła implementuje usługę QEQS, tak aby była odbiorcą zdarzeń QEQS. Te zdarzenia są następnie delegowane do aktualnie aktywnej kontroli źródła pakietu VSPackage. Aktywna pakietu VSPackage kontroli źródła implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> metody i. Metody `IVsQueryEditQuerySave2` interfejsu są zwykle wywoływane bezpośrednio przed rozpoczęciem edycji dokumentu po raz pierwszy i bezpośrednio przed zapisaniem dokumentu.

## <a name="queryeditquerysave-events"></a>Zdarzenia QueryEditQuerySave
 Pakietu VSPackage kontroli źródła musi obsługiwać zdarzenia QEQS przez implementację `IVsQueryEditQuerySave2` interfejsu i niezbędnych metod. Poniżej znajduje się krótki opis dwóch metod, które pakietu VSPackage muszą zaimplementować co najmniej. Rzeczywista implementacja musi być zgodna z logiką modelu kontroli źródła.

### <a name="queryeditfiles-method"></a>QueryEditFiles, Metoda
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>Jest wywoływana, gdy dowolny projekt lub Edytor chce zmodyfikować plik. W idealnym przypadku ta metoda jest wywoływana *przed* zmodyfikowaniem pliku i po jego zapisaniu. Po wywołaniu `IVsQueryEditQuerySave2::QueryEditFiles` Metoda sprawdza, czy dane znajdują się pod kontrolą źródła, czy muszą zostać wyewidencjonowane, oraz czy można je ponownie załadować. Jeśli w okolicznościach nie można edytować plików, `IVsQueryEditQuerySave2::QueryEditFiles` Metoda nakazuje programowi wywołującemu anulowanie edycji. Istnieje również możliwość określenia trybu wywołania przez obiekt wywołujący. W trybie dyskretnym ta metoda wykonuje akcję tylko wtedy, gdy nie powoduje wyświetlania żadnego interfejsu użytkownika. Jeśli nie można uniknąć tego interfejsu, należy zwrócić flagę w celu wskazania problemu.

 Metoda zachowuje się w sposób transakcyjny; oznacza to, że jeśli Edycja zostanie anulowana w jednym pliku, Edycja zostanie anulowana dla wszystkich plików. Na odwrót, jeśli Edycja jest dozwolona, jest dozwolona dla wszystkich plików. Jeśli ta metoda umożliwia edytowanie jednokrotne dla danego zestawu plików, musi zawsze zezwalać na edycję w kolejnych wywołaniach dla tego samego zestawu plików. Pętla zezwalania na edycję będzie kontynuowana do momentu zamknięcia, zapisania i ponownego załadowania plików; do momentu zmiany atrybutów (właściwości); lub do momentu zmiany pakietu kontroli źródła. Przypadki, które należy wziąć pod uwagę podczas implementowania `IVsQueryEditQuerySave2::QueryEditFiles` metody, obejmują wiele plików, pliki specjalne, anulowanie z użytkownika i edycję w pamięci.

### <a name="querysavefiles-method"></a>QuerySaveFiles, Metoda
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>Jest wywoływana, gdy dowolny projekt lub Edytor wymaga zapisania zestawu plików. Po wywołaniu `IVsQueryEditQuerySave2::QuerySaveFiles` Metoda sprawdza, czy te pliki są tylko do odczytu i czy znajdują się pod kontrolą źródła. Jeśli pliki wymagają wyewidencjonowania, wywołanie jest delegowane do pakietu kontroli źródła. Jeśli okoliczności uniemożliwiają zapisywanie plików, `IVsQueryEditQuerySave2::QuerySaveFiles` Metoda musi poinformować Edytor, aby anulować operację zapisywania. Podobnie jak w przypadku `IVsQueryEditQuerySave2::QueryEditFiles` metody obiekt wywołujący może określić tryb wywoływania. W trybie dyskretnym ta metoda wykonuje akcję tylko wtedy, gdy nie powoduje wyświetlania żadnego interfejsu użytkownika. Jeśli nie można uniknąć tego interfejsu, należy zwrócić flagę w celu wskazania problemu.

 Ta metoda musi działać w sposób transakcyjny; oznacza to, że jeśli zapis zostanie anulowany w jednym pliku, operacja zapisywania zostanie anulowana dla wszystkich plików. Z drugiej strony, jeśli zapis jest dozwolony, musi być dozwolony dla wszystkich plików. Podobnie jak w przypadku `IVsQueryEditQuerySave2::QueryEditFiles` metody, przypadki, które należy wziąć pod uwagę podczas implementowania `IVsQueryEditQuerySave2::QuerySaveFiles` metody, obejmują wiele plików, pliki specjalne, anulowanie z użytkownika i edycję w pamięci.

## <a name="see-also"></a>Zobacz też
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
