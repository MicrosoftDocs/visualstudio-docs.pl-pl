---
title: Ochrona dokumentów w rozwiązaniach na poziomie dokumentu
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- restricted permissions [Office development in Visual Studio]
- permissions [Office development in Visual Studio]
- workbooks [Office development in Visual Studio], restricted permissions
- Office documents [Office development in Visual Studio], restricted permissions
- documents [Office development in Visual Studio], restricted permissions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6c5f019907495c3cad3fddef501455aedf345bb2
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2019
ms.locfileid: "71253810"
---
# <a name="document-protection-in-document-level-solutions"></a>Ochrona dokumentów w rozwiązaniach na poziomie dokumentu
  Funkcji ochrony programu Microsoft Office Word i Microsoft Office Excel można użyć w projektach na poziomie dokumentu. Te funkcje blokują nieautoryzowanym użytkownikom wprowadzanie zmian do chronionych części dokumentu.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Za pomocą programu Excel można włączać i wyłączać ochronę, gdy skoroszyt jest otwarty w projektancie. Przy użyciu programu Word można włączyć ochronę tylko poza projektantem. W czasie wykonywania można programowo włączyć lub wyłączyć ochronę dla programów Word i Excel.

 Po włączeniu ochrony dokumentów w dokumencie otwartym w projektancie wszystkie formanty są usuwane z **przybornika** lub stają się niedostępne i nie można przeciągać niczego z okna **źródła danych** do dokumentu.

## <a name="serverdocument-and-protected-documents"></a>ServerDocument i chronione dokumenty
 Jeśli dokument jest chroniony, nie można uzyskać dostępu do pamięci podręcznej danych spoza dokumentu. Nie można użyć <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> klasy do pobierania lub manipulowania danymi, które są buforowane w chronionym dokumencie, lub przy użyciu innych metod <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> klasy.

## <a name="word-document-protection-in-the-designer"></a>Ochrona dokumentów programu Word w projektancie
 W przypadku dodania ochrony do dokumentu lub szablonu programu Word, gdy jest on otwarty w programie Visual Studio, nie można rozpocząć wymuszania ochrony w projektancie. Dokument jest w trybie projektowania, gdy jest otwarty w programie Visual Studio i musi być w trybie uruchomieniowym przed rozpoczęciem wymuszania ochrony.

 Jeśli jednak tworzysz projekt, który używa istniejącego dokumentu programu Word, który ma włączoną ochronę, dokument jest chroniony, gdy jest otwarty w projektancie. Nie można edytować chronionych części dokumentu, ale nadal można napisać kod w edytorze kodu w celu zautomatyzowania dokumentu. Nie można też skompilować projektu, jeśli włączono ochronę, gdy dokument jest otwarty w programie Visual Studio.

 Można wyłączyć ochronę, gdy dokument jest otwarty w projektancie, aby można było edytować dokument i skompilować projekt. Nie można wyłączyć ochrony kopii w Projektancie podczas debugowania; dokument otwarty podczas debugowania jest oddzielną kopią od samego otwarty w projektancie (kopia wyjściowa jest przechowywana w katalogu *\Bin* dla Visual Basic i katalogu *\bin\debug* dla C#).

 Możesz włączyć ochronę kopii dokumentu, która jest otwierana w projektancie, zamykając projekt w programie Visual Studio, otwierając kopię dokumentu znajdującego się w katalogu projektu i włączając ochronę.

## <a name="enforce-word-document-protection-on-build"></a>Wymuś ochronę dokumentów programu Word podczas kompilacji
 Program Visual Studio uruchamia wymuszanie ochrony dokumentów programu Word i szablonów w procesie kompilacji, dzięki czemu ochrona jest włączona, gdy dokument zostanie otwarty na potrzeby debugowania. Dokument jest chroniony za pomocą pustego hasła.

 Ochrona jest włączana podczas kompilacji, więc jeśli w zdarzeniu dokumentu <xref:Microsoft.Office.Tools.Word.Document.Startup> występuje kod, który może powodować wyjątki lub zmieniać zachowanie aplikacji, ten kod może być poprawnie debugowany. Jeśli po otwarciu dokumentu zostanie włączona ochrona, kod inicjalizacji nie może być debugowany ani przetestowany.

## <a name="setting-the-password"></a>Ustawianie hasła
 Program Visual Studio automatycznie włącza ochronę, ale domyślnie nie udostępnia hasła. Jeśli chcesz, aby ochrona dokumentów miała hasło, musisz ją dodać przed wdrożeniem rozwiązania. Dodanie hasła umożliwia autoryzowanym użytkownikom usuwanie ochrony dokumentu; bez hasła nie można łatwo usunąć ochrony. Aby uzyskać szczegółowe informacje na temat ustawiania hasła, zobacz Pomoc w określonej aplikacji pakietu Office.

## <a name="see-also"></a>Zobacz także
- [Instrukcje: Programowe Włączanie ochrony dokumentów i części dokumentów](../vsto/how-to-programmatically-protect-documents-and-parts-of-documents.md)
- [Przykłady i przewodniki dotyczące programowania pakietu Office](../vsto/office-development-samples-and-walkthroughs.md)
- [Zarządzanie prawami do informacji i rozszerzenia kodu zarządzanego — Omówienie](../vsto/information-rights-management-and-managed-code-extensions-overview.md)
- [Ochrona hasłem w dokumentach pakietu Office](../vsto/password-protection-on-office-documents.md)
- [Instrukcje: Zezwalaj na uruchamianie kodu w tle dokumentów z ograniczonymi uprawnieniami](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)
- [Projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md)
