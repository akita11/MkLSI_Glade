Glade�p�Ђт��̐݌v�֘A�t�@�C��(2017/1/24:akita11)

�X�^���_�[�h�Z���̎g����
1. File->New Lib�Ń��C�u�������쐬�B���̂Ƃ��ATechnology��hibikino.tch���w�肷��i�����Ń��C����`�Ȃǂ��ݒ肳���j
2. File->Import->Import GDS2�ŁAstdcell_v2.gds���w�肷��B���̂Ƃ��ǂݍ��ރ��C�u�������A1.�ō쐬�������C�u�����ɐݒ肷��B�܂���File->Open Library�ŁA�����ɂ��� StdCell_v2���w�肷��B
3. �X�^�Z�������̃��C�u�����ɓǂݍ��܂��̂ŁA������g���ĐV������H(Cellview)������

DRC�t�@�C���̎g����
Verify->DRC->Run DRC (Shift+D)�ŁA"hibikino-drc.py" ���w�肵��DRC��������B
�G���[�������Verify->DRC->View DRC Errors�Ŋm�F�ł���

��H���o�̎g����
Verify->Extract->RunLVE�ŁA"hibikino-ext.py"���w�肷��ƁA���̃Z���ɑ΂���extracted�Ƃ����r���[���ł���B�E����"Net Browser"�ɁA�l�b�g��������A�ǂꂩ��I������ƁA���̃l�b�g�ɑΉ�����I�u�W�F�N�g���n�C���C�g�����B�Ȃ����C�A�E�g�ŁAML1/ML2/POL�ɓ������C���ŏ�����������i������̐���_���Ώې}�`�̒��ɂ��邱�Ɓj���A���̃l�b�g�̃l�b�g���ɂȂ�B�l�b�g���X�g�t�@�C���̏o�͂́AFile->Export->Export CDL�ŁA�i�قځjspice�`���ŏo�͂ł���B
