---
title: Różne pliki
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.newfile
- VS.OpenWith
- MiscellaneousFilesProject
helpviewer_keywords:
- solutions, miscellaneous files
- standalone files
- Solution Explorer, miscellaneous files
- Miscellaneous Files folder
- files [Visual Studio], miscellaneous
ms.assetid: 5b96640b-8efe-48a4-8d0a-1ae3f9587e44
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6fb01d0ce09778866074cc8f303c3e4da60f0de1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668971"
---
# <a name="miscellaneous-files"></a>Różne pliki

Warto użyć edytora programu Visual Studio do pracy z plikami niezależnie od projektu lub rozwiązania. Gdy masz otwarte rozwiązanie, możesz otwierać i modyfikować pliki bez dodawania ich do rozwiązania lub do projektu. Pliki, z którymi chcesz współpracować niezależnie, są nazywane różnymi plikami. Różne pliki są zewnętrzne dla rozwiązań i projektów, nie są uwzględniane w kompilacjach i nie mogą być dołączone do rozwiązania pod kontrolą źródła.

Otwieranie plików niezależnie od projektu lub rozwiązania jest przydatne z różnych powodów. Może istnieć plik, który ma być wyświetlany podczas opracowywania rozwiązań opartych na projekcie, ale nie jest to integralność do rozwoju rozwiązania. Typowe przykłady obejmują uwagi dotyczące programowania lub instrukcje, schemat bazy danych i klipy kodu. Ponadto możesz chcieć utworzyć plik autonomiczny.

![Projekty rozwiązań](../../ide/reference/media/projects_solutions_misc.gif)

Jeśli opcje dla tego folderu są włączone, Eksplorator rozwiązań może wyświetlić folder **różne pliki** . Opcje można ustawić za pomocą [okna dialogowego dokumenty, środowisko, opcje](../../ide/reference/documents-environment-options-dialog-box.md). Po zamknięciu różnego pliku nie jest on kojarzony z żadnym konkretnym rozwiązaniem lub projektem, chyba że jest ona również włączona.

Folder **różne pliki** reprezentuje pliki jako linki. Mimo że ten folder nie jest częścią rozwiązania, podczas otwierania rozwiązania niektóre lub wszystkie inne pliki, które zostały otwarte, gdy rozwiązanie zostało ostatnio zamknięte, są ponownie otwierane, w zależności od ustawień folderu.

> [!NOTE]
> Niektóre pliki, które nie są wyświetlane w folderze **różne pliki** , to pliki, których nie można modyfikować w środowisku IDE, takie jak pliki zip i pliki. doc. IDE nie śledzi plików, które mogą być modyfikowane tylko za pomocą zewnętrznego edytora.

## <a name="commands-available-in-the-ide"></a>Polecenia dostępne w środowisku IDE

Menu, paski narzędzi i polecenia, które zawierają zmiany, na podstawie formatu otwartego pliku. Gdy otworzysz plik tekstowy, pojawi się pasek narzędzi Edytor tekstu, a jego polecenia są dostępne. Jeśli następnie otworzysz plik schematu XML, pojawi się pasek narzędzi schematu XML. Podczas edytowania schematu XML polecenia paska narzędzi edytora tekstu (lub samego paska narzędzi) są niedostępne. Schemat XML jest aktywnym oknem i w związku z tym ma bieżący kontekst zaznaczenia. Po przełączeniu między plikiem projektu a plikiem różne, wszystkie polecenia związane z projektem znikają i są wyświetlane tylko te, które są bezpośrednio powiązane z plikiem różne.

## <a name="folder-display-options"></a>Opcje wyświetlania folderu

Można ustawić opcje wyświetlania dla folderu **różne pliki** , tak aby folder pojawił się, mimo że nie zostały otwarte żadne różne pliki. Plik rozwiązania nie umożliwia trwałego zarządzania listą różnych plików. Używa opcjonalnej funkcji, która pozwala na zapamiętanie listy plików dla użytkownika, ostatnio używanych (MRU).

## <a name="see-also"></a>Zobacz także

- [Tworzenie kodu w programie Visual Studio bez projektów ani rozwiązań](../develop-code-in-visual-studio-without-projects-or-solutions.md)
- [Rozwiązania i projekty](../../ide/solutions-and-projects-in-visual-studio.md)
- [Dokumenty, Środowisko, Opcje — okno dialogowe](../../ide/reference/documents-environment-options-dialog-box.md)