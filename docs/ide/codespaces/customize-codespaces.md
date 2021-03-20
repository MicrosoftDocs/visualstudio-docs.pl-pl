---
title: Dostosuj codespace (wersja zapoznawcza)
description: Dowiedz się więcej na temat dostosowywania codespace.
ms.topic: how-to
ms.date: 09/21/2020
author: gregvanl
ms.author: gregvanl
manager: jmartens
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.workload:
- multiple
monikerRange: vs-2019
ms.openlocfilehash: 0e23ca3255761f4d93f89251d00c12c14aecf7b9
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2021
ms.locfileid: "104672354"
---
# <a name="how-to-customize-a-codespace-preview"></a>Jak dostosować codespace (wersja zapoznawcza)

> [!Important] 
> Od 12 kwietnia 2021 połączenie z usługą GitHub Codespaces z programu Visual Studio 2019 nie będzie już obsługiwane i zostanie zawarta prywatna wersja zapoznawcza. Firma Microsoft koncentruje się na rozwojem środowisk dla chmurowych i opartych na chmurze rozwiązań infrastruktury VDI zoptymalizowanych pod kątem szerokiego zestawu obciążeń programu Visual Studio. Zachęcamy do pracy na naszym [forum społeczności deweloperów](https://developercommunity.visualstudio.com/home) dla programu Visual Studio, aby uzyskać informacje na temat przyszłych informacji o zaplanowanych i związanych z planami. 

Usługa GitHub Codespaces zapewnia pełne środowisko programistyczne w chmurze. W przypadku programowania opartego na systemie Windows za pomocą programu Visual Studio 2019 Domyślne wystąpienia usługi GitHub Codespaces oferują doskonały punkt wyjścia, ale można również dostosować środowisko dla określonego projektu.

## <a name="installed-software"></a>Zainstalowane oprogramowanie

System Windows codespaces jest wyposażony w wiele platform i narzędzi, które są już zainstalowane, dzięki czemu możesz zacząć od razu rozpocząć pracę. W poniższej tabeli wymieniono aplikacje i funkcje dostępne we wszystkich środowiskach codespace systemu Windows.

| Aplikacja                                         | Alias ścieżki | Wersja            |
|---------------------------------------------|------------|--------------------|
| .NET                                        | Nie dotyczy        | 4.8                |
| Środowisko uruchomieniowe platformy .NET Core                           | dotnet     | 2,1, 3,1           |
| Zestaw .NET Core SDK                               | dotnet     | 2,1, 3.1.3, 3.1.4  |
| Interfejs wiersza polecenia platformy Azure                                   | AZ         | 2.5                |
| Narzędzia Chocolatey                                  | choco      | 0.10.15            |
| CMake                                       | CMAKE      | 3,17               |
| Git                                         | git        | 2,26               |
| Kompilacja firmy Microsoft                             | MSBuild    | 16,7               |
| Microsoft SQL Server Express Edition 2019   | Nie dotyczy        | 15,0               |
| Ninja                                       | Ninja      | 1.8.2              |
| Node.js                                     | węzeł       | 12,16              |
| NPM                                         | npm        | 6,14               |
| Python                                      | python     | 3.7                |
| Menedżer pakietów VC                          | vcpkg      | 2020,02            |
| Zestaw SDK systemu Windows                                 | Nie dotyczy        | 10.0.18362         |

Powyższa lista nie jest wyczerpująca i wyklucza wiele narzędzi instalowanych przez program Visual Studio (na przykład IISExpress). Składnik może mieć również inną wersję pomocniczą lub poprawek niż podana powyżej.

Szczegółowe informacje na temat wstępnie zainstalowanych platform i narzędzi znajdują się w poniższej sekcji [dotyczącej zainstalowanych programów dotyczących oprogramowania](#installed-software-specifics) .

## <a name="modifications-to-a-codespace"></a>Modyfikacje elementu codespace
 
Po utworzeniu codespace wszystkie zmiany w tym konkretnym codespace są utrwalane, gdy wystąpienie codespace jest dostępne w witrynie GitHub Codespaces. Można klonować dodatkowe repozytoria, narzędzia instalacyjne i generatory aplikacji oraz dodać inne zasoby programistyczne i te modyfikacje zostaną zachowane nawet wtedy, gdy codespace zostanie zawieszone. Jednak po usunięciu codespace wszystkie modyfikacje zostaną utracone.

> [!NOTE]
> Po usunięciu codespace wszystkie zmiany w lokalnym repozytorium (oczekujące lub zatwierdzone) w codespace zostaną utracone. Przed usunięciem codespace upewnij się, że zostały wypchnięte zmiany repozytorium do lokalizacji zdalnej.

Po nawiązaniu połączenia z codespace za pomocą programu Visual Studio można użyć terminalu programu Visual Studio do uruchamiania narzędzi wiersza polecenia. Można użyć programu PowerShell lub wiersza polecenia systemu Windows z podwyższonym poziomem uprawnień w ramach konta administratora lokalnego. Aby dowiedzieć się więcej o terminalu programu Visual Studio, zapoznaj się z [blogiem dotyczącym anonsowania terminalu programu Visual Studio](https://devblogs.microsoft.com/visualstudio/say-hello-to-the-new-visual-studio-terminal/).

## <a name="customize-a-codespace"></a>Dostosowywanie środowiska codespace

Rzeczywista wartość usługi GitHub Codespaces jest dostępna w przypadku tworzenia unikatowych, powtarzalnych środowisk programistycznych w chmurze dopasowanej do własnej pracy oraz Twojego zespołu. Kompilując przy użyciu domyślnego wystąpienia usługi GitHub Codespaces, możesz dostosować, co jest zainstalowane i skonfigurowane podczas tworzenia nowego codespace.

W następnych sekcjach opisano dwie metody konfiguracji codespace przy użyciu *.devcontainer.js* i *.devinit.jsna* plikach. Te pliki umożliwiają skonfigurowanie struktur instalacji i narzędzi dla codespace oraz dodanie ich do repozytorium, a każda osoba tworząca codespace na podstawie Twojego repozytorium będzie mieć to samo zdalne środowisko programistyczne.

## <a name="customize-with-devcontainerjson"></a>Dostosuj przy użyciu devcontainer.jsna

Po utworzeniu codespace usługi GitHub Codespaces wyszukuje [*devcontainers.jsw*](https://code.visualstudio.com/docs/remote/devcontainerjson-reference) pliku w katalogu głównym repozytorium i używa ustawień w programie w celu dostosowania codespace lub wystąpień klienta łączących się z nim (w przeglądarce — edytorze Base, Visual Studio lub Visual Studio Code). Większość *devcontainer.jsw* ustawieniach ma zastosowanie do codespaces opartych na systemie Linux lub dwóch innych klientów, ale niektóre z nich są dostępne dla systemów Windows Codespaces i Visual Studio.

*devcontainer.jsw* pliku można umieścić w jednym z dwóch miejsc w repozytorium:

1. *{Repository-root}/.devcontainer.jsna*
2. *{Repository-root}/.devcontainer/devcontainer.json*

*W witrynie* GitHub Codespaces są obsługiwane następującedevcontainer.jswłaściwości. Ustawienie Visual Studio Code określonych właściwości jest przydatne, jeśli zamierzasz nawiązać połączenie z usługą codespace przy użyciu innych klientów oprócz programu Visual Studio. 

* `extensions` — Tablica rozszerzeń [Visual Studio Code Marketplace](https://marketplace.visualstudio.com/vscode) , które powinny być zainstalowane.
* `settings`  -Zestaw [ustawień Visual Studio Code](https://code.visualstudio.com/docs/getstarted/settings) , które mają zostać zastosowane.
* `forwardPorts`-Port lub tablica portów, które powinny być automatycznie przekazywane lokalnie, gdy codespace jest uruchomiony.
* `postCreateCommand` -Ciąg polecenia lub listę argumentów polecenia do uruchomienia po utworzeniu codespace.

> [!NOTE]
> **devcontainer.js** plików są również używane do obsługi Visual Studio Code [zdalnego tworzenia](https://code.visualstudio.com/docs/remote/remote-overview)i mają dodatkowe właściwości, które nie zostały omówione w tym dokumencie. Te dodatkowe właściwości są bezpiecznie dodawane do pliku, ale zostaną zignorowane przez Codespaces. Aby uzyskać więcej informacji, zobacz [devcontainer.json Reference](https://code.visualstudio.com/docs/remote/devcontainerjson-reference) on Code.VisualStudio.com.

## <a name="customize-with-devinit"></a>Dostosuj przy użyciu devinit

[devinit](../../devinit/getting-started-with-devinit.md) to narzędzie wiersza polecenia zawarte w systemie Windows codespaces, które umożliwia Instalowanie platform i narzędzi w środowisku. Można go uruchomić ręcznie z wiersza polecenia (), `devinit run -t require-dotnetcoresdk` ale jego rzeczywista moc polega na tworzeniu niestandardowego [ *.devinit.jsw*](../../devinit/devinit-json.md) pliku, aby jednolicie konfigurować codespace po każdym utworzeniu.

`devinit` obejmuje zestaw narzędzi do instalowania określonych elementów, takich jak SQL Server i interfejs wiersza polecenia platformy Azure, a także do uruchamiania ogólnych menedżerów pakietów, takich jak czekolady, npm i vcpkg. Pełną listę narzędzi można znaleźć `devinit` w dokumentacji [dostępnych narzędzi](../../devinit/devinit-tool-list.md) .

### <a name="devinitjson"></a>devinit.jsna

Aby można było uruchomić `devinit` wiersz polecenia bezpośrednio, zalecamy utworzenie [*devinit.jsw*](../../devinit/devinit-json.md) plikach konfiguracji, które opisują zestaw `devinit` narzędzi do uruchomienia. 

Na przykład, aby zainstalować [zestaw .NET Core SDK](/dotnet/core/sdk), *.devinit.js* będzie wyglądać następująco:

```json
{
    "run": [
        {
            "comments": "We need the .NET Core SDK."
            "tool": "require-dotnetcoresdk"
        }
    ]
}
```

Podczas tworzenia *.devinit.jsw* pliku w katalogu głównym projektu, będzie on używany podczas uruchamiania `devinit init` . Domyślnie program `devinit.exe` szuka pliku w następujących lokalizacjach:

1. *{Current-Directory} \\.devinit.jsna*
2. *{Current-Directory} \\.devinit\devinit.jsna*

### <a name="running-devinit-when-creating-a-codespace"></a>Uruchamianie devinit podczas tworzenia codespace

Można wydać Codespaces GitHub do uruchomienia `devinit` po utworzeniu codespace przy użyciu `postCreateCommand` właściwości w *devcontainers.jsna* pliku. Jak wspomniano powyżej, serwis GitHub Codespaces szuka *devcontainer.jsw* pliku w sklonowanym repozytorium, aby można było dostosować wystąpienie codespace lub klienta, a następnie uruchomi wszystkie polecenia opisane we `postCreateCommand` właściwości.

Po określeniu `devinit init` program `devinit` zostanie uruchomiony przy użyciu *devinit.jsw* konfiguracji.

```json
{
  "postCreateCommand": "devinit init"
}
```

### <a name="an-example"></a>Przykład

Poniżej przedstawiono prosty przykład instalowania narzędzia wiersza polecenia programu .NET Core Entity Framework `dotnet-ef` .

**devcontainer.json**

Zawartość *.devcontainer.jsw* pliku w katalogu głównym repozytorium. 

```json
{
  "postCreateCommand": "devinit init"
}
```

**devinit.jsna**

Zawartość *.devinit.js* pliku. Ten plik musi znajdować się w tym samym folderze co *.devcontainer.js*.

```json
{
    "run": [
        {
            "comments": "Install the Entity Framework tools",
            "tool": "dotnet-toolinstall",
            "input": "dotnet-ef",
        }
     ]
}
```

Więcej przykładów można znaleźć `devinit` na `devinit` [liście przykładów](../../devinit/sample-readme.md).

## <a name="port-forwarding"></a>Przekierowywanie portów

Usługa GitHub Codespaces zapewnia dostęp do aplikacji i usług działających w środowiskach zdalnych przy użyciu funkcji przekazywania portów. Domyślnie żadne porty nie są przekazywane ze względów bezpieczeństwa. Można jednak określić niektóre porty, które mają być otwierane w codespace.

### <a name="configure-port-forwarding"></a>Konfigurowanie przekierowania portów

Jeśli istnieje co najmniej jeden port, który powinien być przekazywany domyślnie dla danego repozytorium, można go skonfigurować w *devcontainer.js* przy użyciu `forwardPorts` właściwości.

* `forwardPorts` -Port lub tablica portów, które powinny być automatycznie przekazywane lokalnie, gdy środowisko jest uruchomione.

## <a name="installed-software-specifics"></a>Informacje o zainstalowanych oprogramowaniu

### <a name="microsoft-sql-server"></a>Microsoft SQL Server

Microsoft SQL Server 2019 Express Edition jest dostępna i uruchomiona jako Usługa lokalna (LocalDB) w środowisku Codespace systemu Windows. Bieżący użytkownik, który jest używany przez aplikację i Terminal programu Visual Studio, ma uprawnienia administratora SQL do programu SQL Server. Aby administrować serwerem, musisz użyć programu PowerShell w terminalu programu Visual Studio lub innych narzędzi wiersza polecenia, takich jak `dotnet-ef` . Obecnie SQL Server Management Studio i inne narzędzia administracji zdalnej są niedostępne.

#### <a name="example-connection-string"></a>Przykładowe parametry połączenia

Poniżej znajduje się przykład parametrów połączenia w celu nawiązania połączenia z lokalnym serwerem MS SQL.

```csharp
"Server=(LocalDB);Integrated Security=true;"
```

### <a name="azure-cli"></a>Interfejs wiersza polecenia platformy Azure

Interfejs wiersza polecenia platformy Azure jest instalowany we wszystkich środowiskach Codespace systemu Windows i jest dostępny w ścieżce jako `az` .

#### <a name="using-azure-resources"></a>Korzystanie z zasobów platformy Azure

Jeśli używasz tożsamości Azure Active Directory do uwierzytelniania aplikacji na potrzeby zasobów platformy Azure, musisz najpierw zalogować się do platformy Azure z terminala programu Visual Studio. Aby się zalogować, należy użyć polecenia CLI platformy Azure `login` z przepływem logowania urządzenia (jak pokazano w poniższym przykładzie). Po zalogowaniu aplikacja i sesja terminala powinny mieć możliwość korzystania z tej tożsamości.

```powershell
> az login --use-device-code
```

Więcej informacji można znaleźć w `az login` [dokumentacji](/cli/azure/reference-index#az_login)interfejsu wiersza polecenia platformy Azure.

## <a name="see-also"></a>Zobacz też

- [Co to jest GitHub Codespaces?](codespaces-overview.md)
- [Jak używać programu Visual Studio z codespace](use-visual-studio-with-codespaces.md)