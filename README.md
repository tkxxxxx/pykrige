# pykrige
プロシージャ：DrawFromStationInfo

実際にSurferを実行しているプロシージャ：CreateGridData

sInputFile：ContourStInfo_Temp.txt ← 測定局XMLの<StationData>の<Station>の<LNG>と<LAT>と<Value>を抽出して、
CSVに変換したもの
sOutPutFile：SurferOut.dat

dXmin：SurfingSetting.xmlの<xMin>
dXmax：最東端の経度を平面直角座標にしたもの
dYmin：SurfingSetting.xmlの<yMin>
dYmax：最北端の緯度を平面直角座標にしたもの
dNumCols：グリッドの列数

dNumRows：グリッドの行数

SurferApp.GridData(DataFile:=sInputFile _
                 , OutGrid:=sOutPutFile _
                 , Algorithm:=Surfer.SrfGridAlgorithm.srfKriging _
                 , KrigVariogram:=SurferApp.NewVarioComponent(VarioType:=VarioType _
                                                            , AnisotropyRatio:=AnisotropyRatio _
                                                            , AnisotropyAngle:=AnisotropyAngle _
                                                              ) _
                 , xMin:=dXmin, xMax:=dXmax, yMin:=dYmin, yMax:=dYmax _
                 , NumCols:=dNumCols, NumRows:=dNumRows _
                 , ShowReport:=False _
                 , OutFmt:=Surfer.SrfGridFormat.srfGridFmtXYZ _
                 )
