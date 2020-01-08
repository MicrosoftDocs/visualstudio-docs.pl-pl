---
title: Fragmenty kodu XML
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 348dbf64-3f09-4fff-b47a-a7ecdf3221cc
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a2f2bcdd0c28d7b4b99c92d3346b32ed34aa92a0
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592324"
---
# <a name="xml-snippets"></a>Fragmenty kodu XML

Edytor XML oferuje funkcję, nazywaną *fragmentami kodu XML*, która umożliwia szybsze tworzenie plików XML. Można ponownie użyć fragmentów kodu XML, wstawiając je do plików. Możesz również generować dane XML na podstawie schematu definicji schematu XML (XSD).

## <a name="reusable-xml-snippets"></a>Fragmenty kodu XML wielokrotnego użytku

Edytor XML zawiera wiele fragmentów kodu, które obejmują niektóre typowe zadania. Dzięki temu można łatwiej tworzyć pliki XML. Na przykład jeśli tworzysz schemat XML przy użyciu fragmentów "element sekwencji typu złożonego" i "element typu prostego", wstawi następujący tekst XML do pliku. Następnie należy zmienić wartość `name` tak, aby odpowiadała Twoim potrzebom.

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

Fragmenty kodu można wstawiać na dwa sposoby. Polecenie **Wstaw fragment** kodu wstawia fragment kodu XML w pozycji kursora. Element **przestrzenny z** poleceniem otacza fragment kodu XML wokół zaznaczonego tekstu. Oba polecenia są dostępne w podmenu **IntelliSense** w menu **Edycja** lub w menu po kliknięciu prawym przyciskiem myszy w edytorze.

Aby uzyskać więcej informacji, zobacz [How to: Use XML defragments](../xml-tools/how-to-use-xml-snippets.md).

## <a name="schema-generated-xml-snippets"></a>Fragmenty kodu XML generowane przez schemat

Edytor XML umożliwia również generowanie fragmentu kodu XML na podstawie schematu XML. Ta funkcja umożliwia wypełnienie elementu elementami XML wygenerowanymi na podstawie informacji o schemacie dla tego elementu. Aby uzyskać więcej informacji, zobacz [jak: generować fragment kodu XML ze schematu XML](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md).

## <a name="create-new-xml-snippets"></a>Utwórz nowe fragmenty kodu XML

Oprócz fragmentów kodu, które są domyślnie dołączone do programu Visual Studio, można również tworzyć własne fragmenty kodu XML i korzystać z nich. Aby uzyskać więcej informacji, zobacz [How to: Create XML defragments](../xml-tools/how-to-create-xml-snippets.md).

## <a name="see-also"></a>Zobacz także

- [Fragmenty kodu w programie Visual Studio](../ide/code-snippets.md)
- [Edytor XML](../xml-tools/xml-editor.md)
