Glade�p�Ђт��̐݌v�֘A�t�@�C��(2017/1/24:akita11)

�X�^�Z���쐬���̎w�j
StdCell���C�u�������J���A�����̃X�^�Z��(inv1.gex�Ȃ�)�ɑ΂��āA�ȉ��̏C���E�ǉ����s���Ă����B
�E���̂̕ύX(������_v2.gex�����Binv1_v2.gex -> inv1 �Ȃ�)
�Elayout�ł̐M�������x��������̕ύX�i���͂�IA, IB, ...��I����n�܂�B�o�͂̓Q�[�g��O�A�t���b�v�t���b�v��Q��QB�j
�E��H�}(schematics)�̍쐬�i�M������layout�ɂ��킹��BnMOS/pMOS��StdCell���C�u��������nch/pch���A�d����bacis���C�u��������VDD/GND���g�p����j
�E�V���{��(symbol)�̍쐬�i�ȉ��̓_�ɗ���: inv1��symbol���Q�l�Ɂj
  - �O���b�h��1um�P�ʂƂ��āA���Ȃ��Ƃ��l�b�g�i�Ԃ��l�p�j�̓O���b�h�ɏ悹��i�\�Ȕ͈͂ł��ׂĂ̐}�`���j
  - �l�b�g����layout, schematics�ɂ��킹��
  - �S�̂̑傫���́Ainv1�̂��̂�ڈ��Ɂi�ɒ[�ɑ傫��or�������Ȃ�Ȃ��悤�Ɂj
  - �S�̂̒��S���قڌ��_�ɗ���悤�ɔz�u����
  - cellName, instName�AText���쐬����"Label Use"��device label/inst label��I�сAsize��1.0��
  - �O�g��boundary�̒����`�ň͂�

�X�^���_�[�h�Z���̎g����
1. File->New Lib�Ń��C�u�������쐬�B���̂Ƃ��ATechnology��hibikino.tch���w�肷��i�����Ń��C����`�Ȃǂ��ݒ肳���j
2. File->Import->Import GDS2�ŁAstdcell_v2.gds���w�肷��B���̂Ƃ��ǂݍ��ރ��C�u�������A1.�ō쐬�������C�u�����ɐݒ肷��B�܂���File->Open Library�ŁA�����ɂ��� StdCell_v2���w�肷��B
3. �X�^�Z�������̃��C�u�����ɓǂݍ��܂��̂ŁA������g���ĐV������H(Cellview)������

DRC�t�@�C���̎g����
Verify->DRC->Run DRC (Shift+D)�ŁA"hibikino-drc.py" ���w�肵��DRC��������B
�G���[�������Verify->DRC->View DRC Errors�Ŋm�F�ł���

��H���o�̎g����
Verify->Extract->RunLVE�ŁA"hibikino-ext.py"���w�肷��ƁA���̃Z���ɑ΂���extracted�Ƃ����r���[���ł���B�E����"Net Browser"�ɁA�l�b�g��������A�ǂꂩ��I������ƁA���̃l�b�g�ɑΉ�����I�u�W�F�N�g���n�C���C�g�����B�Ȃ����C�A�E�g�ŁAML1/ML2/POL�ɓ������C���ŏ�����������i������̐���_���Ώې}�`�̒��ɂ��邱�Ɓj���A���̃l�b�g�̃l�b�g���ɂȂ�B�l�b�g���X�g�t�@�C���̏o�͂́AFile->Export->Export CDL�ŁA�i�قځjspice�`���ŏo�͂ł���B

��H�}����
�EMOS��StdCell_v2���̃Z��nch/pch���g���B
�E���o�͂́ACreate->Pin�Ńs���Ƃ��āA���̂����č쐬�B
�EVDD/GND���́Abasic���C�u��������vdd/gnd���g���B�܂��͓��o�͂Ɠ������s���Ƃ��č쐬����B
�E�����̒[�q�i�Ԃ��l�p�j��Wire�Ō��ԁB
�Ȃ�Wire�͍ŏ��̓l�b�g�������Ă��Ȃ����ACheck Cellview����ƃl�b�g�������B
�Ȃ����Ă���͂��Ȃ̂ɂȂ����Ă��Ȃ��i�����Ă���j�A�Ƃ����G���[���o�邱�Ƃ����邪�A�ēxCheck Cellview����Ǝ��邱�Ƃ�����i�䋓���j�B
�[�_��wire��2��ڂ��N���b�N����ƁAwire�z�����I���̂ŁA����łȂ����Ă��邩�͔��f�ł���i�[�_��ŃN���b�N���Ȃ���wire�z���������j�B
File->Export��Export CDL�Łi�قځjspice�`���̃l�b�g���X�g���o�͂ł���B

LVS�̂�����
1.���C�A�E�g("layout")���J���A���̎菇�ŉ�H���o�B"extracted"�r���[�����������B
2."extracted"�r���[���J���A��������Verify->LVS->Run LVS��LVS�����s�B��ʂ̉E���Ł��ŉ�H�}����export�����l�b�g���X�g(CDL�`��)���w�肷��B
3.LVS�����{�����B�Ȃ�MOS�g�����W�X�^�̃T�C�Y�̕s��v�͌��o����Ȃ��͗l�i�ڍז��m�F�j�B

PCell
Pcell(parameterized cell)�Ƃ́AMOS�g�����W�X�^�Ȃǂ̗v�f���i���A���̌`��p�����[�^�i�Q�[�g���Ȃǁj���w�肵�āA�����I�Ƀ��C�A�E�g���쐬����@�\�B
(1)nMOS/pMOS�p
1.nmos_master.py��pmos_master.py���ǂ����ɒu���A���ϐ�PYTHONPATH���A���̃f�B���N�g���ɐݒ肷��i�Ȃ��ꍇ�͍쐬�A���ɂ���ꍇ�͒ǉ��j�B�܂��͂�����Glade�̃f�B���N�g��(�E�E�E/glade_win64/�Ȃ�)�ɒu���B
2.New->Cell��Cell���쐬����Ƃ��A"CellView is a Pcell"���`�F�b�N���A"Pcell script"�ɁA������*.py���w�肵�AOK����ƁAnmos_master�܂���nmos_master��layout���쐬�����B�����̃T�C�Y�͕W���l�ō쐬�����B�i���̃Z����super master�ƌĂԁj
3.�g�������Z��(layout)�ŁA�C���X�^���X�쐬(i)�ŁACellName��h_nmos�܂���h_pmos��I�сA ���̂Ƃ�"Instance Property"�^�u�ŁAl�i�Q�[�g���j�Aw�i�Q�[�g���j�Am�i�t�B���K�[���j�Apoly_con�i�Q�[�g�ɃR���^�N�g��ł��j���w�肵�ăC���X�^���X���쐬����ƁA���̃p�����[�^�̐��@��MOS�g�����W�X�^���u�����B�i���܂��쐬����Ȃ��ꍇ������悤�����A��������쐬��A�C���X�^���X�̃v���p�e�B���炱���̃p�����[�^���C������΁A����ɉ������T�C�Y��MOS�g�����W�X�^�ɂȂ�j

(2)�R���^�N�g�EVIA�p
�ȉ��̂��̂�����B����������E�c�ɕ��ׂ�R���^�N�gorVIA�̌���nx,ny�Ŏw�肷��B
�Epolycon_master.py : POL-ML1+�R���^�N�g(CNP)
�Encon_master.py : nACT-ML1+�R���^�N�g(CNA)
�Epcon_master.py : pACT-ML1+�R���^�N�g(CNA)
�Eml1via_master.py : ML1-ML2+VIA

Glade���상��
DisplayOption->Miscellaneous��Always pop up option dialog���͂����ƁAMove�Ȃǂ̂��тɃI�v�V������ʂ��\������Ȃ��iF3�œK�X�\���ł���j
