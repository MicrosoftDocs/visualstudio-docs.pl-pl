---
title: Fragmentów kodu XML
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 348dbf64-3f09-4fff-b47a-a7ecdf3221cc
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 66736431b295f974bda1ca855d88cd5f5f868e7d
ms.sourcegitcommit: 3ca33862c1cfc3ccb83de3e95f1e69e860ab143a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57526158"
---
# <a name="xml-snippets"></a>Fragmentów kodu XML

Edytor XML oferuje funkcję o nazwie *fragmentów kodu XML*, który pozwala szybciej tworzyć pliki XML. Można ponownie użyć fragmentów kodu XML, wstawiając je do plików. Można również wygenerować dane XML, oparte na schemacie języka (XSD) definicji schematu XML.

## <a name="reusable-xml-snippets"></a>Do ponownego użycia fragmentów kodu XML

Edytor XML zawiera wiele fragmentów kodu, które obejmują niektóre typowe zadania. Dzięki temu można łatwiej tworzyć pliki XML. Na przykład jeśli zostały tworzenia schematu XML, przy użyciu fragmentów "Złożonych typów sekwencji Element" i "Proste Element Type" wstawia następujący tekst XML do pliku. Następnie należy zmienić `name` wartości do własnych potrzeb.

```xml
<xs:element name="name">
  <xs:complexType>
    <xs:sequence>
      <xs:element name="name">
        <xs:simpleType>
          <xs:restriction base="xs:string"></xs:restriction>
        </xs:simpleType>
      </xs:element>
    </xs:sequence>
  </xs:complexType>
</xs:element>
```

Fragmenty kodu można wstawić na dwa sposoby. **Wstaw fragment kodu** polecenia wstawia fragment kodu XML w położeniu kursora. **Otocz** polecenia opakowuje fragment kodu XML wokół zaznaczonego tekstu. Oba polecenia są dostępne albo z **IntelliSense** podmenu w obszarze **Edytuj** menu lub menu kliknij prawym przyciskiem myszy w edytorze.

Aby uzyskać więcej informacji, zobacz [jak: Używanie fragmentów kodu XML](../xml-tools/how-to-use-xml-snippets.md).

## <a name="schema-generated-xml-snippets"></a>Wygenerowany schemat fragmentów kodu XML

Edytor XML ma również możliwość Generowanie fragmentu kodu XML na podstawie schematu XML. Ta funkcja umożliwia wypełnić element z elementów XML wygenerowany na podstawie informacji o schemacie dla tego elementu. Aby uzyskać więcej informacji, zobacz [jak: Generowanie fragmentu kodu XML na podstawie schematu XML](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md).

## <a name="create-new-xml-snippets"></a>Tworzenie nowych fragmentów kodu XML

Oprócz fragmenty kodu, które są dołączone do programu Visual Studio domyślnie można również tworzyć i używanie własnych fragmentów kodu XML. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie fragmentów kodu XML](../xml-tools/how-to-create-xml-snippets.md).

## <a name="see-also"></a>Zobacz także

- [Fragmenty kodu w programie Visual Studio](../ide/code-snippets.md)
- [Edytor XML](../xml-tools/xml-editor.md)