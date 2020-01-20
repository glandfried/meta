i# go-dataset

The database is about the public GO games at [https://online-go.com](https://online-go.com)

This database is divided into two repository, one for each source of information:

0. **moves-ogs-database**
The first 12.000.000 `.sgf` files offered by OGS.
*Only public games have information* (around 8 millions files).

0. **output-ogs-database**
The result of public and private games before oct 2013. This iformation is usefull to estimate skill of player.

## Repo: moves-ogs-database

The [OGS](https://online-go.com) plataform offers `.sgf` files which contains the moves made by players that played public games.
The Smart Game Format ([SGF](https://www.red-bean.com/sgf/user_guide/)) is a file format used for storing records of board games.

The first 12.000.000 `.sgf` files offered by OGS:

0. files\_moves\_sgf.tar.gz.partaa
0. files\_moves\_sgf.tar.gz.partab
 
You could find this files attached at the last release.

**Only public games have information** (i.e. only 60% of the files, around 8 millions files). This files where download around in 2018.

### Data

The most important feature stored in the files are the movement made by players, algongside context information.

An example:

```sgf
(;FF[<File Format>]
GM[<Type of Game>]
DT[<YYYY-MM-DD>]
PC[OGS: http://online-go.com/game/<Game ID>]
PB[<Black's nikename>]
PW[<White's nikename>]
BR[<Black's skill>]
WR[<White's skill>]
TM[<Total seconds to play>]
RE[<Result>]
SZ[<Size>]
KM[<Komi>]
RU[<Rules>]
;B[<1st black's move>]
;W[<1st white's move>]
;B[<2nd black's move>]
;W[<2nd white's move>]
;B...
)
```

The reported ability is not the ability they had at the time of playing but the ability they had at the time of downloading the files.

## Repo: output-ogs-dataset

The [OGS](https://online-go.com) plataform offers an API where download public information of games and players.

We store this information as python's dictionary at pickle files. They have a lot of information. The main information can be summarized with with this function:
:
```python
def reduce_games(game): 
    res = {}
    res['id'] = game['id']
    res['annulled'] = game['annulled']
    res['black'] = int(game['black'])
    res['white'] = int(game['white'])
    res['order'] = [int(game['white_lost']),int(game['black_lost'])]
    res['outcome'] = game['outcome']
    res['handicap'] = game['handicap']
    res['komi'] = game['komi']
    res['ranked'] = game['ranked']
    res['width'] = game['width']
    res['started'] = game['started']
    res['ended'] = game['ended']
    res['tournament'] = not game['tournament'] is None
    return res
```


