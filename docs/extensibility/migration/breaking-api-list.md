---
title: Istotne zmiany interfejsu API w wersji Visual Studio 2022 (wersja zapoznawcza)
description: Dowiedz się więcej o zmianach interfejsu API, które powodują niepowodzenie kompilacji istniejących rozszerzeń programu VS podczas migracji rozszerzeń do wersji Visual Studio 2022 (wersja zapoznawcza).
ms.date: 06/08/2021
ms.topic: reference
author: leslierichardson95
ms.author: lerich
manager: jmartens
monikerRange: vs-2022
ms.workload:
- vssdk
ms.openlocfilehash: 9427b7a75ad53fc9a0795b249d96431113aba36d
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2021
ms.locfileid: "112308794"
---
# <a name="breaking-api-changes-in-visual-studio-2022"></a>Istotne zmiany interfejsu API w Visual Studio 2022 r.

[!INCLUDE [preview-note](../includes/preview-note.md)]

W przypadku migrowania rozszerzenia do programu Visual Studio 2022 zmiany istotne wymienione w tym miejscu mogą mieć na Ciebie wpływ.

## <a name="reference-assemblies-no-longer-installed"></a>Zestawy odwoływek nie są już zainstalowane

Wiele zestawów, do których można się odwoływać, które program MSBuild rozpoznał z Visual Studio katalogu instalacyjnego, nie jest już zainstalowany. Należy użyć narzędzia NuGet, aby uzyskać zestawy Visual Studio SDK, których potrzebujesz. Aby [uzyskać szczegółowe instrukcje dotyczące tej czynności, zobacz Modernize](update-visual-studio-extension.md#modernize-your-vsix-project) projects (Modernizacja projektów).

## <a name="removed-apis"></a>Usunięto interfejsy API

W Visual Studio 2022 r. usunięto wiele interfejsów API w ramach Visual Studio przyszłości. Listę usuniętych interfejsów API można znaleźć na stronie [Lista usuniętych interfejsów API.](removed-api-list.md)

## <a name="interop-breaking-changes"></a>Zmiany dotyczące łamania zasad międzyplatplatowych

Wiele naszych interfejsów API uległo zmianie w Visual Studio 2022 r., zazwyczaj z prostymi zmianami, które można łatwo uwzględnić w kodzie.

Aby zarządzać zmianami, planujemy udostępnić nowy mechanizm dystrybucji zestawów międzyoptykowych. W szczególności w Visual Studio 2022 r. i innych zapewniamy pojedynczy zestaw międzyoptykowy z definicjami dla wielu popularnych interfejsów Visual Studio publicznego. Ten zestaw zawiera definicje zarządzane dla wielu interfejsów Visual Studio odchodzi od wielu zestawów międzyoptykowych. Nowy zestaw międzyopłacowy jest dystrybuowany za pośrednictwem `Microsoft.VisualStudio.Interop` pakietu NuGet.

Jednak składniki Visual Studio, które są używane głównie w kontekstach natywnych i mają małą liczbę zmian przerywania, nadal będą mieć własne zestawy międzyoptymalne (na przykład zestaw debugera nadal będzie VisualStudio.Debugger.Interop.dll tak samo jak obecnie). W każdym przypadku zestawy można następnie przywoływać z aplikacji, tak jak obecnie.

Jest to znacząca zmiana i oznacza, że rozszerzenia korzystające z interfejsów API w tym nowym podejściu i zestawu nie są zgodne ze starszymi wersjami usługi Visual Studio przy użyciu poprzedniego zestawu międzyoptykowego.

Ma to kilka bardzo ważnych zalet, które ułatwią aktualizowanie rozszerzenia do Visual Studio 2022 r.:

- Wszelkie uszkodzone interfejsy API staną się błędami czasu kompilacji, co ułatwi ich znalezienie i naprawienie.
- Wystarczy zaktualizować kod, który używa interfejsu API, który został przerwany w Visual Studio 2022 r.
- Nie będzie można przypadkowo użyć starego, teraz uszkodzonego interfejsu API.

Ogólnie rzecz ujmuje to w wyniku bardziej stabilną wersję Visual Studio dla wszystkich użytkowników. Główną wadą tego podejścia jest to, że zarządzane zestawy nie będą mogły działać zarówno w wersji Visual Studio 2019, jak i Visual Studio 2022 bez kompilowania kodu raz dla każdej docelowej Visual Studio wersji.

Podczas pracy nad błędami kompilacji spowodowanymi różnicami interfejsu API między programem Visual Studio 2019 a Visual Studio 2022 możesz znaleźć interfejs API lub wzorzec, który został wymieniony poniżej, ze wskazówkami, jak go naprawić.

### <a name="int-or-uint-where-intptr-is-expected"></a>`int` lub `uint` tam, `IntPtr` gdzie jest to oczekiwane

Oczekujemy, że będzie to bardzo powszechny błąd. Aby Visual Studio 2022 r. był procesem 64-bitowym, niektóre z naszych interfejsów API międzyoptykowych muszą zostać naprawione, gdzie zakładały, że wskaźnik może zmieścić się w 32-bitowej całkowitej wartości, aby faktycznie użyć wartości o rozmiarze wskaźnika.

Przykładowy błąd:

> Argument 3: nie można przekonwertować z "out uint" na "out System.IntPtr"

Wystarczy zaktualizować kod, aby oczekiwał lub podać albo gdzie lub kiedy był używany `IntPtr` `UIntPtr` do rozwiązania `int` `uint` problemu.

Przykładowa poprawka:

```diff
-shell.LoadLibrary(myGuid, myFlags, out uint ptrLib);
+shell.LoadLibrary(myGuid, myFlags, out IntPtr ptrLib);
```

### <a name="an-interop-type-defined-in-two-assemblies"></a>Typ międzyopłaciowy zdefiniowany w dwóch zestawach

Gdy kompilator języka C# zgłasza błąd, że typ, z którym korzystasz, jest zdefiniowany w dwóch zestawach, prawdopodobnie odwołujesz się do zestawu z wersji Visual Studio 2019 zestawu SDK, do których nie należy się już odwoływać.

Przykładowy błąd:

> błąd CS0433: Typ "IVsDpiAware" istnieje zarówno w pliku "Microsoft.VisualStudio.Interop, Version=17.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a" i "Microsoft.VisualStudio.Shell.Interop.16.0.DesignTime, Version=16.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a'

Zapoznaj się z naszą [tabelą ponownego mapowania zestawu](migrated-assemblies.md) referencyjnego, aby zobaczyć, która nazwa zestawu jest preferowaną nazwą w Visual Studio 2022 r.
Biorąc pod uwagę dwa zestawy o nazwie w powyższym przykładowym błędzie i patrząc na tę tabelę, zwróć uwagę, że `Microsoft.VisualStudio.Interop` jest to nowa nazwa zestawu. Następnie poprawka będzie usuwać odwołanie do `Microsoft.VisualStudio.Shell.Interop.16.0.DesignTime` z projektu.

W niektórych przypadkach oferujemy pakiet Visual Studio wersji 2022 dla przestarzałego zestawu, który zawiera usługi przesyłania dalej typu. Gdy ta opcja jest dostępna,  możesz uaktualnić odwołanie do pakietu do wersji Visual Studio 2022 zamiast go usuwać. Przesyłanie dalej typu rozwiąże błąd kompilatora.

Należy pamiętać, że czasami te odwołania mogą pochodzić z przechodniego odwołania do pakietu i w związku z tym może być trudniejsze do usunięcia niż bezpośrednie odwołanie w pliku projektu. W takich przypadkach upewnij się, że wszystkie odwołania do pakietu bezpośredniego same Visual Studio zestawu SDK 2022. Możesz odwołać się *doproject.assets.js,* aby zidentyfikować łańcuch pakietów odpowiedzialnych za wprowadzenie przestarzałego zestawu. Aktualizowanie odwołania do pakietu przechodniego do wersji Visual Studio 2022 jest tak proste, jak zainstalowanie go jako bezpośredniego odwołania.

Jeśli nie można zmienić drzewa zależności (na przykład ze względu na zależność innej firmy), możesz dodać bezpośrednie odwołanie do pakietu przed programem Visual Studio 2022 i dodać metadane do tego elementu w celu rozwiązania błędu `ExcludeAssets="compile"` `PackageReference` kompilatora. Należy jednak pamiętać, że w przypadku tej techniki rozszerzenie może zachować zależność od zestawu przed Visual Studio 2022 r., a rozszerzenie może działać nieprawidłowo w czasie wykonywania.

### <a name="missing-reference-to-an-interop-assembly"></a>Brak odwołania do zestawu międzyoptykowego

W przypadku odwołania do zestawu, który został skompilowany względem zestawu SDK Visual Studio 2022, może wystąpić błąd z informacjami o braku odwołania do zestawu.

Przykładowy błąd:

> Błąd CS0012 Typ "IVsTextViewFilter" jest zdefiniowany w zestawie, do których nie ma odwołania. Należy dodać odwołanie do zestawu "Microsoft.VisualStudio.TextManager.Interop, Version=7.1.40304.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"

Korzystając z [tabeli ponownego mapowania zestawu referencyjnego,](migrated-assemblies.md)można potwierdzić, że żądany zestaw w rzeczywistości nie jest tym, do których należy się odwołać.

Najlepszym rozwiązaniem jest zaktualizowanie zależności do wersji, która została skompilowana względem zestawu SDK programu Visual Studio 2022, tak aby usunięty zestaw międzyoptykowy nie był już żądany przez kompilator.

W niektórych przypadkach oferujemy pakiet Visual Studio wersji 2022 dla przestarzałego zestawu, który zawiera usługi przesyłania dalej typu. Gdy ta opcja jest dostępna, można dodać odwołanie do pakietu do wersji Visual Studio 2022 przestarzałego pakietu, dzięki czemu usług przesyłania dalej typu rozwiąże błąd kompilatora.

### <a name="iasyncserviceprovider-is-missing"></a>`IAsyncServiceProvider` brakuje

Istnieją dwie definicje tego interfejsu w dwóch przestrzeniach nazw. Tylko jedna z nich była przeznaczona do użycia zarządzanego.

Visual Studio 2019, przestrzeń nazw | Visual Studio 2022, przestrzeń nazw | Zamierzone użycie
--|--|--
Microsoft.VisualStudio.Shell.IAsyncServiceProvider | Microsoft.VisualStudio.Shell.IAsyncServiceProvider | Zużycie kodu zarządzanego
Microsoft.VisualStudio.Shell.Interop.IAsyncServiceProvider | Microsoft.VisualStudio.Shell.COMAsyncServiceProvider.IAsyncServiceProvider | tylko na niskim poziomie międzyplatopsyjnie

Jeśli zostanie wyświetlony błąd o wartości , być może używasz kodu natywnego `IAsyncServiceProvider` (drugiego wiersza). 
Jeśli tak, możesz zaktualizować przestrzeń nazw do nowej przestrzeni nazw lub przełączyć się do bardziej przyjaznego dla zarządzania interfejsu.

### <a name="dte-and-_dte-type-cast-failures"></a>`DTE` błędy `_DTE` rzutowania typów i

`DTE` i `_DTE` są interfejsami. Jeden pochodzi od drugiego. Jednak w Visual Studio 2022 r. są zamieniane typy podstawowe i pochodne.
Powoduje to, że niektóre przypisania typów lub rzutowania nie powiodą się.

Oznacza to również, że w przypadku użycia funkcji `new DTE()` należy teraz użyć . `new _DTE()`

### <a name="missing-argument-on-a-method-invocation"></a>Brak argumentu w wywołaniach metody

Kilka metod nie deklaruje już domyślnych argumentów dla parametrów opcjonalnych w interfejsie API międzyoptyku.
Jeśli wystąpi błąd dotyczący brakującego argumentu dla wywołania międzyoptyku COM, a parametr wywołuje typ, poprzednią wartością domyślną zdefiniowaną przez interfejs API międzyopcyjki programu Visual Studio 2019 mógł być , dlatego rozważ dodanie jako argumentu w celu rozwiązania błędu `object` `""` `""` kompilacji.

W razie wątpliwości co do tego, jaki był domyślny argument, spróbuj przełączyć kontekst usługi językowej z Visual Studio 2022 na Visual Studio 2019, aby uzyskać intellisense ze starszymi zestawami międzyoptyków, aby zobaczyć, jaki był argument domyślny, a następnie dodać go jawnie do kodu. Będzie ona nadal działać prawidłowo w przypadku kompilowania dla Visual Studio 2019 r., ale teraz będzie kompilowana dla Visual Studio 2022 r.

Przykładowa poprawka:

```diff
-process4.Attach2();
+process4.Attach2("");
```
