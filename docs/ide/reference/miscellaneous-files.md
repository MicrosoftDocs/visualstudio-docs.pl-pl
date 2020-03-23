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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 793500faf217c74772506b4b7394d926447ffd40
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75585300"
---
# <a name="miscellaneous-files"></a>Różne pliki

Można użyć edytora Visual Studio do pracy nad plikami niezależnie od projektu lub rozwiązania. Po otwarciu rozwiązania można otwierać i modyfikować pliki bez dodawania ich do rozwiązania lub do projektu. Pliki, z którymi chcesz pracować niezależnie, są nazywane różnymi plikami. Różne pliki są zewnętrzne do rozwiązań i projektów, nie są uwzględniane w kompilacjach i nie mogą być dołączone do rozwiązania pod kontrolą źródła.

Otwieranie plików niezależnie od projektu lub rozwiązania jest przydatne z różnych powodów. Być może masz plik, który chcesz wyświetlić podczas opracowywania rozwiązania opartego na projekcie, ale nie jest to integralną częścią rozwoju rozwiązania. Typowe przykłady obejmują uwagi dotyczące rozwoju lub instrukcje, schemat bazy danych i klipy kodu. Ponadto można utworzyć plik autonomiczny.

![Projekty rozwiązań](../../ide/reference/media/projects_solutions_misc.gif)

Eksplorator rozwiązań może wyświetlać folder **Różne pliki** dla plików, jeśli opcje folderu są włączone. Opcje można ustawić w [oknie dialogowym Dokumenty, Środowisko, Opcje](../../ide/reference/documents-environment-options-dialog-box.md). Po zamknięciu pliku różne, nie jest skojarzony z żadnym określonym rozwiązaniem lub projektu, chyba że opcja jest włączona dla tego, jak również.

Folder **Różne pliki** reprezentuje pliki jako łącza. Chociaż ten folder nie jest częścią rozwiązania, po otwarciu rozwiązania niektóre lub wszystkie różne pliki, które zostały otwarte podczas ostatniego zamknięcia rozwiązania, są ponownie otwierane, w zależności od ustawień folderu.

> [!NOTE]
> Niektóre pliki, które nie są wyświetlane w folderze **Różne pliki,** to pliki, których nie można modyfikować w środowisku IDE, takie jak pliki zip i pliki doc. IDE nie śledzi plików, które mogą być modyfikowane tylko za pośrednictwem zewnętrznego edytora.

## <a name="commands-available-in-the-ide"></a>Polecenia dostępne w IDE

Menu, paski narzędzi i polecenia, które zawierają, zmieniają się w zależności od formatu otwieranego pliku. Na przykład po otwarciu pliku tekstowego zostanie wyświetlony pasek narzędzi Edytor tekstu, a jego polecenia są dostępne. Jeśli następnie otworzysz plik schematu XML, zostanie wyświetlony pasek narzędzi Schemat XML. Podczas edytowania schematu XML polecenia na pasku narzędzi Edytora tekstu (lub sam pasek narzędzi) są niedostępne. Schemat XML jest aktywnym oknem i jako taki ma bieżący kontekst wyboru. Po przełączeniu między plikiem projektu a plikiem różnych, wszystkie polecenia związane z projektem znikają i pojawiają się tylko te, które są bezpośrednio związane z plikiem różnych.

## <a name="folder-display-options"></a>Opcje wyświetlania folderów

Można ustawić opcje wyświetlania folderu **Różne pliki,** tak aby folder był wyświetlany, nawet jeśli nie otwarto żadnych różnych plików. Plik rozwiązania nie zarządza trwale listą różnych plików. Używa opcjonalnej funkcji, która pozwala na zapamiętanie listy plików na użytkownika, ostatnio używanej (MRU).

## <a name="see-also"></a>Zobacz też

- [Tworzenie kodu w programie Visual Studio bez projektów ani rozwiązań](../develop-code-in-visual-studio-without-projects-or-solutions.md)
- [Rozwiązania i projekty](../../ide/solutions-and-projects-in-visual-studio.md)
- [Dokumenty, środowisko, opcje — Okno dialogowe](../../ide/reference/documents-environment-options-dialog-box.md)
