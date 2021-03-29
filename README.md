# Lag et enkelt maurspill
## Introduksjon @unplugged
I dette spillet skal mauren finne veien hjem
## Test startkoden
Her er litt ferdig kode. Test spillet og ta en kikk på koden.
```template
let mySprite: Sprite = null
scene.setBackgroundColor(7)
tiles.setTilemap(tilemap`level1`)
mySprite = sprites.create(img`
    ........ff.....fff........
    ..ffff....f...ff..........
    ......f...f...f...........
    .......f..f.ff....fffff...
    ...fff..ffff.....fdeeeef..
    f.feef.fdeef.ff.fdeeeeeef.
    .feeeffdeeeffeefdeeeeeeeef
    .feeeffdeeeffeefdeeeeeeeef
    f.feef.fdeef.ff.fdeeeeeef.
    ...fff..fffff....fdeeeef..
    .......f..f..f....fffff...
    ......f...f...f...........
    ..ffff....f....fff........
    ........ff................
    `, SpriteKind.Player)
controller.moveSprite(mySprite)
scene.cameraFollowSprite(mySprite)
```
## Start spillet med forklaring
Finn ``||game:splash||`` fra ``||game:Game-menyen||``. Sett blokken inn i koden under ``||variables:set mySprite to||``. Skriv inn tekst, f.eks "Finn veien hjem"
```blocks
let mySprite: Sprite = null
scene.setBackgroundColor(7)
tiles.setTilemap(tilemap`level1`)
mySprite = sprites.create(img`
    ........ff.....fff........
    ..ffff....f...ff..........
    ......f...f...f...........
    .......f..f.ff....fffff...
    ...fff..ffff.....fdeeeef..
    f.feef.fdeef.ff.fdeeeeeef.
    .feeeffdeeeffeefdeeeeeeeef
    .feeeffdeeeffeefdeeeeeeeef
    f.feef.fdeef.ff.fdeeeeeef.
    ...fff..fffff....fdeeeef..
    .......f..f..f....fffff...
    ......f...f...f...........
    ..ffff....f....fff........
    ........ff................
    `, SpriteKind.Player)
game.splash("Finn veien hjem!")
controller.moveSprite(mySprite)
scene.cameraFollowSprite(mySprite)
```
## Når mauren er over maurtuen skal vi flytte oss ned i maurtua
Da trenger vi ``||scene:Scene-blokken||`` ``||scene:on sprite of kind player overlaps||``. Denn blokken plasserer du et sted ved siden av ``||loops:on start||``. Endre flisen til maurhode med svart bakgrunn (se hint)
```blocks
scene.onOverlapTile(SpriteKind.Player, assets.tile`myTile`, function (sprite, location) {

})
```
## Vi bytter flisekart
Finn ``||scene:set tilemap to||`` fra ``||scene:Scene-menyen|`` og plasser denne inn i ``||scene:on sprite of kind player overlaps||``-blokken. Trykk på kartet og velg det mørke bilde (level2) 
```blocks
scene.onOverlapTile(SpriteKind.Player, assets.tile`myTile`, function (sprite, location) {
    tiles.setTilemap(tilemap`level2`)
})
```
## Vi plasserer mauren øverst i tuen
Finn ``||scene:place on random||`` fra ``||scene:Scene-menyen|`` og plasser denne under ``||scene:on sprite of kind player overlaps||``-blokken. Endre flisen til myTile0 (se hint)
```blocks
scene.onOverlapTile(SpriteKind.Player, assets.tile`myTile`, function (sprite, location) {
    tiles.setTilemap(tilemap`level2`)
    tiles.placeOnRandomTile(mySprite, assets.tile`myTile0`)
})
```
## Hva skal skje når vi kommer hjem?
Innerst i maurtuen er sjeftmauren. Når vi overlapper med den er vi hjemme og har vunnet. Finn ``||scene:on sprite of kind player overlaps||``. Denne blokken plasserer du et sted ved siden av ``||loops:on start||``. Endre flisen til maurhode med brun bakgrunn (se hint) 
```blocks
 scene.onOverlapTile(SpriteKind.Player, assets.tile`myTile1`, function (sprite, location) {

})
```
## Game over
Finn ``||game:game over||``-blokken og sett den inn i ``||scene:overlapp med maur(brun bakgrunn)||``
```blocks
 scene.onOverlapTile(SpriteKind.Player, assets.tile`myTile1`, function (sprite, location) {
    game.over(true, effects.confetti)
})
```
## Ferdig
Gratulerer! du har laget et enkelt maurspill
```jres
{
    "image14": "hwQaAA4AAAAAAPAADwAAAA8AAP8AAAAADwDw7g8AAAAPAO/u/gAAAA8A7+7+AAAA8AD///8AAAAADwD/AADwAADw8N0PD/AADwDf7v3w/wAPAO/u/gDwAPD/7+7+DwAAAAD////wAAAA8AD/8AAPAADw8O4PD/AA8A/w7g/wAAD/AAD/AAAPAA8A8N0PAA8ADwDf7v0ADwAA8O3u3g/wAADw7u7uDw8AAPDu7u4PDwAA8O7u7g8PAADw7u7uDwAAAADv7v4AAAAAAPDuDwAAAAAAAP8AAAAA",
    "image15": "hwQaAA4AAAAAAAD/AAAAAAAA8O4PAAAAAADv7v4AAAAA8O7u7g8AAPDw7u7uDwAA8PDu7u4PAADw8O7u7g8AAA/w7e7eDwAA8ADf7v0A8ADwAPDdDwDwAPAAAP8AAP8AAA/w7g/wDwAP8PDuDw8AAPAAD/8ADwAAAA////8AAAAA8O/u/v8PAA8A7+7+APAA/w/f7v0A8AAP8PDdDw8AAA8AAP8A8AAAAAD///8ADwAAAO/u/gDwAAAA7+7+APAAAADw7g8A8AAAAAD/AADwAAAA8AAPAAAA",
    "image16": "hwQaAA4AAAAAAPAADwAAAAAAAP8AAAAAAADw7g8A8AAAAO/u/gDwAAAA7+7+APAAAAD///8ADwAAAAD/APAAAA8A8N0PDwAAD/Df7v0AAAAPD+/u/gAAAPDw7+7+DwAAAA/////wAADwAAD/8AAPAA8A/+4PD/AAAPDw7g/wAAAA8AD/APAAAAAP8N0P8AAA8ADf7v0ADwDw8O3u3g8PAPDw7u7uDwAA8PDu7u4PAAAA8O7u7g8AAADw7u7uDwAAAADv7v4AAAAAAPDuDwAAAAAAAP8AAAAA",
    "image17": "hwQOABoAAAAAAAD//wDwAAAPAAAAAAAAAAAAAA8AD/D/8P8AAAAAAAAAAAAP8AAPAAAAAAAAAAAAAADwAA/wAAD//w8AAAAAAPD/AP//DwDw7e7+AAAAAA/v/vDt/vAP3+7u7g8AAADw7v7f7v7v/u3u7u7+AAAA8O7+3+7+7/7t7u7u/gAAAA/v/vDt/vAP3+7u7g8AAAAA8P8A//8AAPDt7v4AAAAAAAAA8AAP/wAA//8PAAAAAAAAAA8ADwAPAAAAAAAAAAAAAPAAAA8A/wAAAAAAAAAA8P8PAP8AAPD/AAAAAAAAAA==",
    "image18": "hwQaAA4AAAAAAPAADwAAAAAAAP8AAAAA8ADw7g8ADwDwAO/u/gAPAPAA7+7+AA8A8AD///8ADwAADwD/APAAAADw8N0PDwAADwDf7v0A8AAPAO/u/gDwAPD/7+7+/w8AAAD///8AAAAA8AD/8AAAAADw8O4PDwAA8A/w7g/wAAD/AAD/AAAPAA8A8N0PAA8ADwDf7v0ADwAA8O3u3g8AAADw7u7uDwAAAPDu7u4PAAAA8O7u7g8AAADw7u7uDwAAAADv7v4AAAAAAPDuDwAAAAAAAP8AAAAA",
    "image19": "hwQaAA4AAAAAAAD/AAAAAAAA8O4PAAAAAADv7v4AAAAA8O7u7g8AAADw7u7uDwAAAPDu7u4PDwAA8O7u7g8PAPDw7e7eDw8A8ADf7v0ADwAAD/DdD/AAAAAPAP8ADwAAAA/w7g8PAAAP8PDu/wDwAPAAD/8AAA8AAA/////wAAAA8O/u/g8PAAAA7+7+8PAAAADf7v0P8AAA8PDdDwDwAAAPAP8AAAAA8AD///8AAAAPAO/u/gAAAA8A7+7+AAAADwDw7g8AAAAAAAD/AAAAAAAA8AAPAAAA",
    "image20": "hwQOABoAAAAAAAAA/w8AAP8A8P8PAAAAAAAAAAD/APAAAA8AAAAAAAAAAAAA8ADwAPAAAAAAAAAA8P//AAD/8AAPAAAAAAAAAO/u3g8AAP//AP8PAAAAAPDu7u798A/v3g/v/vAAAADv7u7u3u/+7+797+4PAAAA7+7u7t7v/u/u/e/uDwAAAPDu7u798A/v3g/v/vAAAAAA7+7eDwDw//8A/w8AAAAAAPD//wAAD/AADwAAAAAAAAAAAAAA8AAP8AAAAAAAAAAAAP8P/w/wAPAAAAAAAAAAAAAA8AAADwD//wAAAAAAAA==",
    "image21": "hwQaAA4AAAAAAPAADwAAAAAAAP8AAAAA8ADw7g8ADwDwAO/u/gAPAPAA7+7+AA8A8AD///8ADwAADwD/APAAAADw8N0PDwAADwDf7v0A8AAPAO/u/gDwAPD/7+7+/w8AAAD///8AAAAA8AD/8AAAAADw8O4PDwAA8A/w7g/wAAD/AAD/AAAPAA8A8N0PAA8ADwDf7v0ADwAA8O3u3g8AAADw7u7uDwAAAPDu7u4PAAAA8O7u7g8AAADw7u7uDwAAAADv7v4AAAAAAPDuDwAAAAAAAP8AAAAA",
    "image22": "hwQOABoAAAAA/w8AAADwAAAAAAAAAAAAAADwAAAADwDwDwAAAAAAAAAAAA8A8AD/DwAAAAAAAAAAAADwAA/wAAD//w8AAAAAAPD/AP//DwDw7e7+AAAAAA/v/vDt/vAP3+7u7g8AAADw7v7f7v7v/u3u7u7+AAAA8O7+3+7+7/7t7u7u/gAAAA/v/vDt/vAP3+7u7g8AAAAA8P8A///wAPDt7v4AAAAAAAAAAA8PAP8A//8PAAAAAAAAAADw8AAADwAAAAAAAAAAAAAAAA8PAPD/DwAAAAAAAAAA8P8A8AAAAAAAAAAAAA==",
    "image23": "hwQaAA4AAAAAAAD/AAAAAAAA8O4PAAAAAADv7v4AAAAA8O7u7g8AAADw7u7uDwAAAPDu7u4PAAAA8O7u7g8AAADw7e7eDwAA8ADf7v0A8ADwAPDdDwDwAPAAAP8AAP8AAA/w7g/wDwAA8PDuDw8AAAAAD/8ADwAAAAD///8AAADw/+/u/v8PAA8A7+7+APAADwDf7v0A8AAA8PDdDw8AAAAPAP8A8AAA8AD///8ADwDwAO/u/gAPAPAA7+7+AA8A8ADw7g8ADwAAAAD/AAAAAAAA8AAPAAAA",
    "image24": "hwQOABoAAAAAAAAAAAAPAP8PAAAAAAAAAADw/w8A8PAAAAAAAAAAAAAAAADwAAAPDwAAAAAAAAAA8P//AP8A8PAAAAAAAAAAAO/u3g8AD///AP8PAAAAAPDu7u798A/v3g/v/vAAAADv7u7u3u/+7+797+4PAAAA7+7u7t7v/u/u/e/uDwAAAPDu7u798A/v3g/v/vAAAAAA7+7eDwDw//8A/w8AAAAAAPD//wAAD/AADwAAAAAAAAAAAADw/wAPAPAAAAAAAAAAAADwDwDwAAAADwAAAAAAAAAAAAAADwAAAPD/AAAAAA==",
    "image25": "hwQOABoAAAAAAAAA/wAAAAAAAAAAAAAAAP//AAAPAPD/AAAAAAAAAAAAAA8ADwAPAAAAAAAAAAAAAADwAA/wAAD//w8AAAAAAPD/AP//DwDw7e7+AAAAAA/v/vDt/vAP3+7u7g8AAADw7v7f7v7v/u3u7u7+AAAA8O7+3+7+7/7t7u7u/gAAAA/v/vDt/vAP3+7u7g8AAAAA8P8A//8AAPDt7v4AAAAAAAAA8AAP/wAA//8PAAAAAAAAAA8ADwAPAAAAAAAAAAAA//8AAA8A/wAAAAAAAAAAAAAAAP8AAPD/AAAAAAAAAA==",
    "image26": "hwQOABoAAAAAAAAA/w8AAP8AAAAAAAAAAAAAAAD/APAAAP//AAAAAAAAAAAA8ADwAPAAAAAAAAAA8P//AAD/8AAPAAAAAAAAAO/u3g8AAP//AP8PAAAAAPDu7u798A/v3g/v/vAAAADv7u7u3u/+7+797+4PAAAA7+7u7t7v/u/u/e/uDwAAAPDu7u798A/v3g/v/vAAAAAA7+7eDwDw//8A/w8AAAAAAPD//wAAD/AADwAAAAAAAAAAAAAA8ADwAPAAAAAAAAAAAAAA/w8A8AAA//8AAAAAAAAAAAAAAAD/AAAAAAAAAA==",
    "*": {
        "mimeType": "image/x-mkcd-f4",
        "dataEncoding": "base64",
        "namespace": "myImages"
    }
}
```
```jres
{
    "transparency16": {
        "data": "hwQQABAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA==",
        "mimeType": "image/x-mkcd-f4",
        "tilemapTile": true
    },
    "tile1": {
        "data": "hwQQABAAAAD/////////////////////////////////7//v7v7////+/h7u7v/////v7u7u/////+/u7u7/////7+7u7v/////v7u7u/////+/u7u7////+/h7u7v///+//7+7+/////////////////////////////////////////////w==",
        "mimeType": "image/x-mkcd-f4",
        "tilemapTile": true,
        "displayName": "myTile"
    },
    "tile3": {
        "data": "hwQQABAAAADd3d3d3d3d3d3d3d3d3d3d3d3d3d3d3d3d7d3t7t7d3d3e3h7u7t3d3d3t7u7u3d3d3e3u7u7d3d3d7e7u7t3d3d3t7u7u3d3d3e3u7u7d3d3e3h7u7t3d3e3d7e7e3d3d3d3d3d3d3d3d3d3d3d3d3d3d3d3d3d3d3d3d3d3d3Q==",
        "mimeType": "image/x-mkcd-f4",
        "tilemapTile": true,
        "displayName": "myTile1"
    },
    "tile2": {
        "data": "hwQQABAAAADd3d3d3d3d3d3d3d3d0d3d3bvd3d0d3d3dvd3d293d3d3d3R3d3d3d3d3d3d3d3dHd3d3d3d3d3d3d3d3d3d3d3d3d3dHdHd3d3d3d3d3d293d0d3d3d3dHd3d3d3d3d3d3d3d3d3d3d3d3dHdvdvd3d3d3d293d3d3d3d3d3d3Q==",
        "mimeType": "image/x-mkcd-f4",
        "tilemapTile": true,
        "displayName": "myTile0"
    },
    "level1": {
        "id": "level1",
        "mimeType": "application/mkcd-tilemap",
        "data": "MTAxOTAwMTkwMDAxMDMwMTAxMDEwMTAxMDEwMTAxMDEwMTAxMDEwMTAxMDEwMTAxMDEwMTAxMDEwMTAxMDMwMTAxMDMwMTAxMDMwMTAxMDEwMTAxMDMwMzAxMDEwMTAxMDEwMTAxMDEwMTAxMDEwMTAxMDMwMTAzMDEwMTAxMDEwMzAxMDMwMjAxMDEwMTAzMDIwMzAxMDEwMjAxMDEwMTAzMDEwMTAxMDEwMTAxMDEwMzAxMDMwMTAzMDEwMTAzMDMwMTAxMDEwMTAxMDEwMTAxMDEwMTAxMDEwMjAxMDEwMTAxMDEwMTAxMDEwMTAxMDMwMTAxMDEwMTAxMDMwMTAxMDEwMTAxMDMwMjAxMDEwMTAxMDEwMTAxMDEwMTAzMDMwMzAxMDEwMTAxMDEwMTAxMDEwMTAxMDEwMzAxMDEwMTAxMDEwMTAxMDMwMTAxMDEwMTAxMDEwMTAzMDEwMzAxMDEwMTAxMDEwMTAxMDEwMTAxMDEwMTAxMDEwMzAyMDEwMTAxMDMwMTAxMDEwMTAxMDEwMTAxMDEwMTAxMDEwMTAxMDEwMTAxMDMwMTAxMDEwMTAxMDEwMTAxMDEwMTAxMDEwMTAxMDEwMTAxMDEwMzAxMDEwMTAxMDMwMTAxMDEwMTAxMDEwMTAzMDEwMTAxMDEwMzAxMDIwMTAxMDEwMTAxMDEwMTAxMDIwMTAzMDIwMTAxMDMwMTAxMDEwMTAxMDEwMTAxMDEwMTAxMDEwMzAxMDEwMTAxMDEwMTAxMDEwMTAxMDEwMTAxMDMwMTAxMDEwMTAxMDEwMTAxMDEwMTAxMDEwMTAyMDEwMTAzMDEwMTAxMDEwMzAzMDEwMTAxMDMwMjAxMDEwMTAxMDEwMTAxMDEwMzAxMDEwMTAxMDMwMzAxMDMwMjAzMDMwMTAxMDEwMTAxMDEwMTAxMDEwMTAxMDEwMTAxMDMwMTAxMDEwMTAzMDEwMTAxMDEwMTAxMDEwMTAxMDEwMTAxMDEwMTAxMDEwMTAxMDEwMzAxMDEwMzAxMDEwMTAxMDEwMzA0MDgwOTAxMDMwMTAxMDEwMTAxMDEwMTAxMDEwMTAxMDEwMTAxMDEwMTAzMDEwMTA0MGMwYzBjMDkwMTAxMDEwMTAxMDMwMTAxMDEwMTAxMDMwMTAxMDIwMTAxMDEwMTA0MGMwZTBmMTAwYzA5MDEwMTAxMDIwMTAxMDEwMTAxMDEwMTAxMDEwMTAxMDEwMTAzMDUwYzBkMTIxMTBjMGIwMTAxMDEwMTAxMDEwMTAxMDEwMzAzMDMwMTAxMDEwMTAxMDEwNjBjMTMxNDE1MGMwYTAxMDEwMTAxMDMwMTAxMDEwMTAxMDMwMTAxMDEwMTAxMDEwMjAxMDYwYzBjMGMwYTAxMDEwMjAxMDEwMTAxMDEwMTAxMDEwMTAxMDEwMTAzMDEwMTAxMDEwMTA2MDcwYTAzMDEwMTAxMDEwMTAxMDMwMTAxMDIwMzAzMDEwMTAzMDEwMTAxMDMwMTAxMDEwMTAzMDEwMTAzMDEwMTAxMDEwMTAxMDIwMTAxMDEwMTAyMDMwMTAxMDEwMTAzMDEwMTAzMDEwMTAxMDEwMTAxMDEwMTAxMDEwMTAxMDEwMjAxMDEwMTAxMDEwMTAxMDEwMzAxMDEwMTAxMDEwMTAxMDEwMTAyMDEwMTAyMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDA=",
        "tileset": [
            "myTiles.transparency16",
            "sprites.castle.tileGrass1",
            "sprites.castle.tileGrass2",
            "sprites.castle.tileGrass3",
            "sprites.castle.tilePath1",
            "sprites.castle.tilePath4",
            "sprites.castle.tilePath7",
            "sprites.castle.tilePath8",
            "sprites.castle.tilePath2",
            "sprites.castle.tilePath3",
            "sprites.castle.tilePath9",
            "sprites.castle.tilePath6",
            "sprites.castle.tilePath5",
            "sprites.builtin.forestTiles9",
            "sprites.builtin.forestTiles5",
            "sprites.builtin.forestTiles6",
            "sprites.builtin.forestTiles7",
            "sprites.builtin.forestTiles15",
            "myTiles.tile1",
            "sprites.builtin.forestTiles24",
            "sprites.builtin.forestTiles26",
            "sprites.builtin.forestTiles29"
        ],
        "displayName": "level1"
    },
    "level3": {
        "id": "level3",
        "mimeType": "application/mkcd-tilemap",
        "data": "MTAxMDAwMTAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMA==",
        "tileset": [
            "myTiles.transparency16"
        ],
        "displayName": "level3"
    },
    "level2": {
        "id": "level2",
        "mimeType": "application/mkcd-tilemap",
        "data": "MTAxOTAwMzIwMDAxMDMwMzAzMDMwMzAzMDMwMzAzMGEwYTBhMGEwMzAzMDMwMzAzMDMwMzAzMDMwMzAyMDQwNjA2MDYwNjA2MDYwNjA2MDUwYTBhMGEwYTA0MDYwNjA2MDYwNjA2MDYwNjA2MDUwNzA5MDkwOTBhMGEwYTBhMGEwYTBhMGMwYTBhMDkwOTA5MDkwOTA5MDkwOTA5MDkwODA3MDkwOTA5MGEwYTBhMGEwYTBhMGEwYTBhMGEwOTA5MDkwOTA5MDkwOTA5MDkwOTA4MDcwOTA5MDkwYTBhMDkwOTA5MDkwOTA5MDkwOTA5MDkwOTA5MDkwOTA5MDkwOTA5MDgwNzA5MDkwOTBhMGEwOTA5MDkwOTA5MDkwOTA5MDkwOTA5MDkwOTA5MDkwOTA5MDkwODA3MDkwOTA5MGEwYTA5MDkwOTA5MDkwOTA5MDkwOTA5MDkwOTA5MDkwOTA5MDkwOTA4MDcwOTA5MDkwYTBhMDkwOTA5MDkwOTA5MDkwOTA5MDkwOTA5MDkwOTA5MDkwOTA5MDgwNzA5MDkwOTBhMGEwOTA5MDkwOTA5MDkwOTA5MDkwOTA5MDkwOTA5MDkwOTA5MDkwODA3MDkwOTA5MGEwYTA5MDkwOTA5MDkwOTA5MDkwOTA5MDkwOTA5MDkwOTA5MDkwOTA4MDcwOTA5MDkwYTBhMGEwYTBhMGEwYTBhMGEwYTBhMDkwOTA5MDkwOTA5MDkwOTA5MDgwNzA5MDkwOTBhMGEwYTBhMGEwYTBhMGEwYTBhMGEwYTBhMGEwYTBhMDkwOTA5MDkwODA3MDkwOTA5MGEwYTA5MDkwOTA5MDkwOTA5MGEwYTBhMGEwYTBhMGEwOTA5MDkwOTA4MDcwOTA5MDkwYTBhMDkwOTA5MDkwOTA5MDkwOTA5MDkwOTA5MDkwOTA5MDkwOTA5MDgwNzA5MDkwOTBhMGEwOTA5MDkwOTA5MDkwOTA5MDkwOTA5MDkwOTA5MDkwOTA5MDkwODA3MDkwOTA5MGEwYTBhMGEwOTA5MDkwYTBhMDkwOTA5MDkwOTA5MDkwOTA5MDkwOTA4MDcwOTA5MDkwYTBhMGEwYTBhMGEwYTBhMGEwOTA5MDkwOTA5MDkwOTA5MDkwOTA5MDgwNzA5MDkwOTA5MDkwYTBhMGEwYTBhMGEwYTBhMDkwOTA5MDkwOTA5MDkwOTA5MDkwODA3MDkwOTA5MDkwOTA5MDkwOTA5MDkwYTBhMGEwOTA5MDkwOTA5MDkwOTA5MDkwOTA4MDcwOTA5MDkwOTA5MDkwOTA5MDkwOTA5MGEwYTBhMDkwOTA5MDkwOTA5MDkwOTA5MDgwNzA5MDkwOTA5MDkwOTA5MDkwOTA5MDkwYTBhMGEwOTA5MDkwOTA5MDkwOTA5MDkwODA3MDkwOTA5MDkwOTA5MDkwOTA5MDkwOTA5MGEwYTA5MDkwOTA5MDkwOTA5MDkwOTA4MDcwOTA5MDkwOTA5MDkwOTA5MDkwOTA5MDkwYTBhMDkwOTA5MDkwOTA5MDkwOTA5MDgwNzA5MDkwOTA5MDkwOTA5MDkwOTA5MDkwOTBhMGEwOTA5MDkwOTA5MDkwOTA5MDkwODA3MDkwOTA5MDkwOTA5MDkwOTA5MDkwOTA5MGEwYTBhMDkwOTA5MDkwOTA5MDkwOTA4MDcwOTA5MDkwOTA5MDkwOTA5MDkwOTA5MDkwOTBhMGEwOTA5MDkwOTA5MDkwOTA5MDgwNzA5MDkwOTA5MDkwOTA5MDkwOTA5MDkwOTA5MGEwYTA5MDkwOTA5MDkwOTA5MDkwODA3MDkwOTA5MDkwOTA5MDkwOTA5MDkwOTA5MDkwYTBhMDkwOTA5MDkwOTA5MDkwOTA4MDcwOTA5MDkwOTA5MDkwOTA5MDkwOTA5MDkwYTBhMGEwOTA5MDkwOTA5MDkwOTA5MDgwNzA5MDkwOTA5MDkwOTA5MDkwOTA5MGEwYTBhMGEwYTA5MDkwOTA5MDkwOTA5MDkwODA3MDkwOTA5MDkwOTA5MDkwOTA5MGEwYTBhMGEwYTA5MDkwOTA5MDkwOTA5MDkwOTA4MDcwOTA5MDkwOTA5MDkwOTA5MGEwYTBhMGEwOTA5MDkwOTA5MDkwOTA5MDkwOTA5MDgwNzA5MDkwOTA5MDkwOTA5MDkwYTBhMGEwOTA5MDkwOTA5MDkwOTA5MDkwOTA5MDkwODA3MDkwOTA5MDkwOTA5MDkwYTBhMGEwOTA5MDkwOTA5MDkwOTA5MDkwOTA5MDkwOTA4MDcwOTA5MDkwOTA5MDkwOTBhMGEwYTA5MDkwOTA5MDkwOTA5MDkwOTA5MDkwOTA5MDgwNzA5MDkwOTA5MDkwOTA5MGEwYTA5MDkwOTA5MDkwOTA5MDkwOTA5MDkwOTA5MDkwODA3MDkwOTA5MDkwOTA5MDkwYTBhMDkwOTA5MDkwOTA5MDkwOTA5MDkwOTA5MDkwOTA4MDcwOTA5MDkwOTA5MDkwOTBhMGEwOTA5MDkwOTA5MDkwOTA5MDkwOTA5MDkwOTA5MDgwNzA5MDkwOTA5MDkwOTA5MGEwYTBhMGEwYTA5MDkwOTA5MDkwOTA5MDkwOTA5MDkwODA3MDkwOTA5MDkwOTA5MDkwYTBhMGEwYTBhMGEwYTBhMGEwYTBhMDkwOTA5MDkwOTA4MDcwOTA5MDkwOTA5MDkwOTA5MDkwOTBhMGEwYTBhMGEwYTBhMGEwOTA5MDkwOTA5MDgwNzA5MDkwOTA5MDkwOTA5MDkwOTA5MDkwOTA5MDkwOTA5MGEwYTBhMDkwOTA5MDkwODA3MDkwOTA5MDkwOTA5MDkwOTA5MDkwOTA5MDkwOTA5MGEwYTBhMGEwYTA5MDkwOTA4MDcwOTA5MDkwOTA5MDkwOTA5MDkwOTA5MDkwOTA5MGEwYTBhMGEwYTBhMGEwOTA5MDgwNzA5MDkwOTA5MDkwOTA5MDkwOTA5MDkwOTA5MDkwYTBhMGEwYjBhMGEwYTA5MDkwODA3MDkwOTA5MDkwOTA5MDkwOTA5MDkwOTA5MDkwOTBhMGEwYTBhMGEwYTBhMDkwOTA4MDcwOTA5MDkwOTA5MDkwOTA5MDkwOTA5MDkwOTA5MDkwYTBhMGEwYTBhMDkwOTA5MDgwNzA5MDkwOTA5MDkwOTA5MDkwOTA5MDkwOTA5MDkwOTA5MGEwYTBhMGEwOTA5MDkwODA3MDkwOTA5MDkwOTA5MDkwOTA5MDkwOTA5MDkwOTA5MDkwOTA5MDkwOTA5MDkwOTA4MDcwOTA5MDkwOTA5MDkwOTA5MDkwOTA5MDkwOTA5MDkwOTA5MDkwOTA5MDkwOTA5MDgyMjIyMjIyMjIyMDAwMDIyMjIyMjIyMjIyMjIyMjIyMjIyMDIwMDIwMjIyMjIyMjIyMjIyMjIwMDAwMDAwMDAwMjIyMjIyMjIyMjIyMjIwMjAwMDAwMDAwMjAyMjIyMjIyMjIyMjIyMjAwMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjAyMjAyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMDAyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMDIyMDIyMjIyMjIyMjIyMjIyMjIyMjIyMjIwMDIyMjIyMjIyMjIyMjIyMjIyMjIyMjIwMjIwMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjAwMDAwMDAwMDAyMDIyMjIyMjIyMjIyMjAyMDAwMDAwMDAwMDAwMDAyMDIyMjIyMjIyMDAyMjIyMjIwMjAwMDAwMDIyMjIyMjIyMDIyMDIyMjIyMjIyMjIyMjIyMjIyMjIyMjIwMDIyMjIyMjIyMjIyMjIyMjIyMjIyMjIwMjAwMjAyMjAwMjIyMjIyMjIyMjIyMjIyMjAwMDAwMDAwMjAyMjIyMjIyMjIyMjIyMjIyMDIwMDAwMDAyMDIyMjIyMjIyMjIyMjIyMjIyMjIyMDIwMDIyMjIyMjIyMjIyMjIyMjIyMjIyMjIwMjAwMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjAwMjAyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMDAyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMDIyMDIyMjIyMjIyMjIyMjIyMjIyMjIyMjIwMDIyMjIyMjIyMjIyMjIyMjIyMjIyMjIwMjAwMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjAyMjAyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMDAyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMDIyMDIyMjIyMjIyMjIyMjIyMjIyMjIyMDIwMDIyMjIyMjIyMjIyMjIyMjIyMjIyMDAwMDIwMjIyMjIyMjIyMjIyMjIyMjIyMDAwMDIwMjIyMjIyMjIyMjIyMjIyMjIyMDAwMDIyMjIyMjIyMjIyMjIyMjIyMjIyMDIwMDIyMjIyMjIyMjIyMjIyMjIyMjIyMDIwMDIyMjIyMjIyMjIyMjIyMjIyMjIyMjIwMDIwMjIyMjIyMjIyMjIyMjIyMjIyMjIwMjIwMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjAwMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjAyMjAyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMDAwMDIwMjIyMjIyMjIyMjIyMjIyMjIyMDIwMDAwMDAwMDAwMjIyMjIyMjIyMjIyMjIyMjAyMDAwMDAwMjAyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMDAyMDIyMjIyMjIyMjIyMjIyMjIyMjIyMDAwMDIwMjIyMjIyMjIyMjIyMjIyMjIyMDAwMDAwMjAyMjIyMjIyMjIyMjIyMjIyMDIwMDAwMDAyMjIyMjIyMjIyMjIyMjIyMjIwMDAwMDAyMDIyMjIyMjIyMjIyMjIyMjIyMjAwMDAyMDIyMjIyMjIyMjIyMjIyMjIyMjIyMDAwMDIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMg==",
        "tileset": [
            "myTiles.transparency16",
            "sprites.builtin.forestTiles1",
            "sprites.builtin.forestTiles3",
            "sprites.builtin.forestTiles2",
            "sprites.builtin.forestTiles5",
            "sprites.builtin.forestTiles7",
            "sprites.builtin.forestTiles6",
            "sprites.builtin.forestTiles9",
            "sprites.builtin.forestTiles11",
            "sprites.builtin.forestTiles10",
            "sprites.castle.tilePath5",
            "myTiles.tile3",
            "myTiles.tile2"
        ],
        "displayName": "level2"
    },
    "*": {
        "mimeType": "image/x-mkcd-f4",
        "dataEncoding": "base64",
        "namespace": "myTiles"
    }
}
```



> Open this page at [https://vitenkvinne.github.io/maurspill_veiledning/](https://vitenkvinne.github.io/maurspill_veiledning/)

## Use as Extension

This repository can be added as an **extension** in MakeCode.

* open [https://arcade.makecode.com/](https://arcade.makecode.com/)
* click on **New Project**
* click on **Extensions** under the gearwheel menu
* search for **https://github.com/vitenkvinne/maurspill_veiledning** and import

## Edit this project ![Build status badge](https://github.com/vitenkvinne/maurspill_veiledning/workflows/MakeCode/badge.svg)

To edit this repository in MakeCode.

* open [https://arcade.makecode.com/](https://arcade.makecode.com/)
* click on **Import** then click on **Import URL**
* paste **https://github.com/vitenkvinne/maurspill_veiledning** and click import

## Blocks preview

This image shows the blocks code from the last commit in master.
This image may take a few minutes to refresh.

![A rendered view of the blocks](https://github.com/vitenkvinne/maurspill_veiledning/raw/master/.github/makecode/blocks.png)

#### Metadata (used for search, rendering)

* for PXT/arcade
<script src="https://makecode.com/gh-pages-embed.js"></script><script>makeCodeRender("{{ site.makecode.home_url }}", "{{ site.github.owner_name }}/{{ site.github.repository_name }}");</script>
