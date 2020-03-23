---
title: Tworzenie określonych obiektów docelowych w rozwiązaniach za pomocą programu MSBuild.exe
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, building specific targets in a solution
- msbuild.exe, building specific targets in a solution
- MSBuild, msbuild.exe
ms.assetid: f46feb9b-4c16-4fec-b6e1-36a959692ba3
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 178dfcaf0bdf8296fd271cb7c4e5dd0bbd251d7f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633931"
---
# <a name="how-to-build-specific-targets-in-solutions-by-using-msbuildexe"></a>Jak: Tworzenie określonych celów w rozwiązaniach przy użyciu programu MSBuild.exe

Program *MSBuild.exe* służy do tworzenia określonych obiektów docelowych określonych projektów w rozwiązaniu.

## <a name="to-build-a-specific-target-of-a-specific-project-in-a-solution"></a>Aby zbudować określony cel określonego projektu w rozwiązaniu

1. W wierszu polecenia `MSBuild.exe <SolutionName>.sln`wpisz `<SolutionName>` , gdzie odpowiada nazwę pliku rozwiązania, który zawiera miejsce docelowe, które chcesz wykonać.

2. Określ miejsce `-target:` docelowe po \<przełączeniu w formacie\<ProjectName>: TargetName>. Jeśli nazwa projektu zawiera dowolny `%` `$`ze `@` `;`znaków `.` `(`, `)`, `'`, , `_` , , , lub , zastąpić je w określonej nazwie docelowej.

## <a name="example"></a>Przykład

 Poniższy przykład wykonuje `Rebuild` obiekt `NotInSlnFolder` docelowy projektu, a `Clean` następnie `InSolutionFolder` wykonuje obiekt docelowy projektu, który znajduje się w folderze *newfolder* rozwiązania.

```cmd
msbuild SlnFolders.sln -target:NotInSlnfolder:Rebuild;NewFolder\InSolutionFolder:Clean
```

## <a name="troubleshooting"></a>Rozwiązywanie problemów

Jeśli chcesz zbadać opcje dostępne dla Ciebie, można użyć opcji debugowania dostarczone przez MSBuild, aby to zrobić. Ustaw zmienną `MSBUILDEMITSOLUTION=1` środowiskową i skompiluj rozwiązanie. Spowoduje to powstanie pliku MSBuild o nazwie * \<SolutionName>.sln.metaproj,* który pokazuje wewnętrzny widok rozwiązania w czasie kompilacji. Można sprawdzić ten widok, aby określić, jakie obiekty docelowe są dostępne do kompilacji.

Nie należy tworzyć z tego zestawu zmiennych środowiska, chyba że potrzebujesz tego widoku wewnętrznego. To ustawienie może powodować problemy z tworzeniem projektów w rozwiązaniu.

## <a name="see-also"></a>Zobacz też

- [Odwołanie do wiersza polecenia](../msbuild/msbuild-command-line-reference.md)
- [Odwołanie do budynku MSBuild](../msbuild/msbuild-reference.md)
- [Msbuild](../msbuild/msbuild.md)
- [Koncepcje MSBuild](../msbuild/msbuild-concepts.md)
